---
title: "Weird ssh issue (correct password)"
date: 2019-04-16
forum: Installation &amp; Upgrades
---

### Post by coolcal2 on 2019-04-16
So, hi o/

I bought a server recently and installed ubuntu 18.04 server onto it, however, when I went to log into the server from my pc an issue arose in that I am unable to log into the server.

I have tried changing the config files, changing the user I tried to log in with and using keys.

It appears the ssh is rejecting external logins, not sure what to try thus why I have turned to the community for help,
thanks in advance.

---

### Post by benjaminsaulmcculloch on 2019-04-16
Hey coolcal2,

Do you get any error message when try to login?

---

### Post by TheFu on 2019-04-16
Did you install ssh-server?
Are you using the userid that was created during install?  Don't use root.

---

### Post by SeijiSensei on 2019-04-16
If you're logging in from a Linux client, use "ssh -v" to get more details on your session.  Add more "v's", up to three, for more verbosity.

---

### Post by coolcal2 on 2019-04-16
Error messages, regardless of if the password being correct or not are Access Denied

---

### Post by coolcal2 on 2019-04-16
Ssh is set up correctly, 
I have allowed root to connect. here is my /etc/ssh/sshd_config

```
PermitRootLogin yes 
AuthorizedKeysFile    .ssh/authorized_keys 
PasswordAuthentication yes 
ChallengeResponseAuthentication no 
UsePAM yes 
PrintMotd no # pam does that 
Subsystem    sftp    /usr/lib/ssh/sftp-server
```

the issue appears to be something is not allowing access.

---

### Post by SeijiSensei on 2019-04-16
Does the user have the same UID (e.g., 1000) on both machines?  Are you sure the home directory of the user you're logging in as has the correct permissions?

Just choosing "PermitRootLogin" is not enough to allow root access.  Does the remote's root user have a password?  By default, root never has a password in Ubuntu; that's why the sudo mechanism is used throughout. 

The best approach is to used shared keys: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by coolcal2 on 2019-04-17
Hi, sorry for the late reply. 

I gave all accounts passwords and used puTTYgen for the keys. accounts should have correct permissions.

---

