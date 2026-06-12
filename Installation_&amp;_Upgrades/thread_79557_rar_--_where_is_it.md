---
title: "rar -- where is it?"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by WamBamBoozle on 2005-10-20
Hi. I can't seem to "sudo apt-get install rar unrar" -- I get 

[INDENT]apt-get install rar unrar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate[/INDENT]

I am using the stock apt file from kubuntu breezy but with all the optional repositories uncommented.

---

### Post by fog on 2005-10-20
Add multiverse repositories

---

### Post by Kyral on 2005-10-20
and get the unrar-nonfree package :D

Oh, to add the Multiverse, (and Universe) crack open a terminal and

```
sudo gedit /etc/apt/sources.list
```

And tag "multiverse" onto the end of the lines that say "universe"

Then just save and update apt

---

### Post by bluebyt on 2005-10-20
[QUOTE=Kyral]and get the unrar-nonfree package :D

Oh, to add the Multiverse, (and Universe) crack open a terminal and

```
sudo gedit /etc/apt/sources.list
```

And tag "multiverse" onto the end of the lines that say "universe"

Then just save and update apt[/QUOTE]

Sorry, but did you mean to replace "multiverse" by "universe" ?,
I really want to have unrar-nonfree and the backports doesn't work.

---

### Post by Kyral on 2005-10-20
I meant append it to, add it on to, etc ;D

---

### Post by fog on 2005-10-21
&#913;dd this line to your **/etc/apt/sources.list**
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
Then: [B]sudo apt-get update
[/B] and
**sudo apt-get install rar unrar**

---

### Post by lotusleaf on 2005-10-21
RAR can also be found [here](http://www.rarlab.com/download.htm), the current version of RAR as of this posting is directly downloadable here: [rarlinux-3.5.1.tar.gz](http://www.rarlab.com/rar/rarlinux-3.5.1.tar.gz).

Installation of the above (following downloading of) is as simple as:

```

tar zxvf rarlinux-3.5.1.tar.gz
cd rar
sudo make

```

---

### Post by sonsuzuncu on 2005-10-24
ediz@ubuntu:~$ tar zxvf rarlinux-3.5.1.tar.gz
rar/
rar/file_id.diz
rar/license.txt
rar/Makefile
rar/order.htm
rar/rarfiles.lst
rar/rar.txt
rar/readme.txt
rar/technote.txt
rar/whatsnew.txt
rar/rar
rar/rar_static
rar/unrar
rar/default.sfx
ediz@ubuntu:~$ cd rar
ediz@ubuntu:~/rar$ sudo make
Password:
sudo: make: command not found
ediz@ubuntu:~/rar$ sudo make
sudo: make: command not found

also i'm 5.10 breezy member

---

### Post by elrohir_telperien on 2005-11-06
In response to **sonsuzuncu's** post, you don't have to make/compile rar or unrar. 

It is ready to use when you untar them. (refering to *rar * and *unrar*)

---

### Post by SickTwist on 2005-11-06
sonsuzuncu,
Like the previous poster said, you shouldn't need to make/compile this particular package.

However, I wanted to let you know for future reference that you got an error message because make and the other development tools are not installed by default. To install make, gcc (the compiler), etc:

sudo apt-get install build-essential

---

