---
title: "Never asked to create Root Password!?!"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by CaptainCrunch on 2005-02-08
I just switched to Ubuntu from Fedora Core 3 (god was that a POS).   I went through the installation process rather painlessly, but I never was asked to create a Root password.    Now I'm no Linux expert, but how the heck am I suppose to do anything without Root access?

So the question remains, how on earth do I fix this?   Will putting the Install CD back in fix this?   Am I gonna have to redo everything when I do that?

Thanks in advance.

---

### Post by oracledarren on 2005-02-08
use the sudo command in front of what you would normally do with root and your away.

if you need root you will also need to use this command to set a root password

sudo passwd root

then from computer-sys config-login screen dialogue you will need to set the gdm to allow root logins

once that is done is will allow root to login.

The first method though is more secure and you dont really need to log in as root to achieve anything :)

---

### Post by friez on 2005-02-08
Ubuntu use sudo in stead of root(ie: su /root login)
the password for sudo is your user password
to become root and creat a passwd just due this
```
friez@helfire:~ $ sudo -s
Password:(user password)
root@helfire:~ # passwd <---- now your root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@helfire:~ #

```
 edit @#$% someone beat me 2 it  8)

---

### Post by CaptainCrunch on 2005-02-08
Thanks a lot.    I'll go do that, or shouldn't I?   I'm just so use to using "su" in terminal window/consoles.

Does creating a "root" user make "sudo" not work anymore?

Hmmm....maybe I'll just have to dig my nose into the FAQ's and HOWTO's a bit more.

I definitely like this distro much more than Fedora, that's for damn sure.

Thanks again.

---

### Post by anomie on 2005-02-08
CaptainCrunch, 

I am comfortable with SuSE / redhat, and I am very used to using "su -" frequently in the console. While I appreciate what Ubuntu is trying to do, I just don't feel interested. 

I checked /etc/shadow and found that root didn't have a password, so, like the other posters point out once you give him one you can su again.

---

