# SSH KEYS
## Generating key pair
`ssh-keygen -t rsa -b 4096 -f ssh-key`


> Posible cypher algorithms are rsa dsa ecdsa ed25519
>
> Difference between them are perfomance and compatibility.


```shell
Generating public/private rsa key pair.
Enter file in which to save the key (/home/user/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in ggate-key
Your public key has been saved in ggate-key.pub
The key fingerprint is:
SHA256:
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|       .         |
|       o     . o |
|     o      oo oo|
|      = S  +.+ o*|
|     o ..o+   +o.|
|      =....+o  .E|
|    .o+ +.o.oo  .|
|   ..o..  oBBo. .|
+----[SHA256]-----+
```
## Copying pub key to authorized hosts

### A) SSH-COPY

`ssh-copy-id -i ~/.ssh/id_rsa user@host`

### B) SCP
```bash
scp id_rsa.pub user@remhost:~/.ssh/
ssh user@remhost
cd .ssh
cat id_rsa.pub >> authorized_keys

```
> authorized_keys file should be 600 permissions
## Test login without password

`ssh user@remhost`
