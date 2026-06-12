---
title: "Installing java?"
date: 2011-04-04
forum: Installation &amp; Upgrades
---

### Post by mittygrimsey on 2011-04-04
Alright so i'm new to ubuntu and im having trouble installing java, my mate told me to type this in to the terminal but it came up with an error.

> liam@liam-HP-Vectra:~$ sudo apt-get install sun-java6-jre
[sudo] password for liam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
I asked him what to do and he said he doesn't know.

Thanks in advance :)

---

### Post by Dutch70 on 2011-04-04
Go to software center and search for ubuntu-restricted-extras, click install, and you're done.

Otherwise, open a terminal and put in this command...
```
sudo apt-get install ubuntu-restricted-extras
```

---

