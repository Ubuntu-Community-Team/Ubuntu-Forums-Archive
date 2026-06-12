---
title: "Ssh"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by Aphotic_13 on 2007-03-28
i believe i am doing something wrong with my ssh install.  i just installed Ubuntu 6.10 desktop, and this is where i am at.  does anyone know the proper way to get ssh working? thanks!

```
$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openssh-server has no installation candidate
$
$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate
$
$ sudo apt-get install openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$
$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-client ssh-askpass-gnome
E: Package ssh has no installation candidate
$
$ ssh *myusername*@*myipwashere*
ssh: connect to host *myipwashere* port 22: Connection refused
ed
$
```

---

### Post by Aphotic_13 on 2007-03-28
nm i got it hehe

---

