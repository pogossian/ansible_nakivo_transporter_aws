## Deploying NAKIVO  Transporter to AWS EC2

*Ansible playbook should be ran from same VPC*


1) Clone project

```
git clone https://github.com/pogossian/ansible_nakivo_transporter_aws
```

2) Go to project directory, remove old .git repository and initialize a new one.

```
cd ansible_nakivo_transporter_aws/
rm -rf .git
git init
```

3) Change variables in aws_vars.yml.

  *Verify if download_url is still actual, security_group will be created
  automatically, there is no need to create it in AWS manually*


4) Then we’ll need to store the AWS keys. Since they are sensitive data,
we should use Ansible vault for this.

```
ansible-vault create aws_keys.yml
```

Once open, add the following to it:

```
aws_access_key: AKIAJLHNMCBOITV643UA
aws_secret_key: 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
```

5) Run playbook.

```
ansible-playbook --ask-vault-pass playbook.yml
```
