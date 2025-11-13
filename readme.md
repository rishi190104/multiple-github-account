
#### Generate a SSH Key for all the accounts you want to access

##### Example's for personal account

```bash
ssh-keygen -t ed25519 -C "yourpersonal@gmail.com" -f ~/.ssh/id_github_personal
```
##### Example's for company account

```bash
ssh-keygen -t ed25519 -C "yourcompany@gmail.com" -f ~/.ssh/id_github_company
```

#### Add it to your ssh agent

```bash
eval "$(ssh-agent -s)"
```

```bash
ssh-add ~/.ssh/id_github_personal
ssh-add ~/.ssh/id_github_company
```
#### Create or edit SSH Config

```bash
code ~/.ssh/config
```

#### Add this in the config file

```bash
# Personal GitHub
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_github_personal
  IdentitiesOnly yes
  
# Company Github
Host github-company
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_github_company
  IdentitiesOnly yes
  
```

#### Add SSH Key to your respective Github Accounts

```bash
cat ~/.ssh/id_github_personal.pub
cat ~/.ssh/id_github_company.pub
```
##### The above commands will give you the ssh keys, copy the entire key and add in your respective github accounts

#### Test SSH connection

```bash
ssh -T git@github-personal
ssh -T git@github-company
```
##### Expected Output

```rust
Hi personal-username! You've successfully authenticated...
Hi company-username! You've successfully authenticated...
```

#### Clone your repo using SSH

```bash
git clone git@github-personal:username/repo_name.git
```

```bash
git clone git@github-company:username/repo_name.git
```

##### Use git@Host  = The host you have named in the config

# Congratulation you have successfully setup multiple github account access in vscode
