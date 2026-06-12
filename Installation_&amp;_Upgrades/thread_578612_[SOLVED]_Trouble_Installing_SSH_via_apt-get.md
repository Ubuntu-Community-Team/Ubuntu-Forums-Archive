---
title: "[SOLVED] Trouble Installing SSH via apt-get"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by winkerbean on 2007-10-17
Hi,
I'm trying to install OpenSSH server on 7.04 Xubuntu via apt-get.  However, I get the following message:
[INDENT]After unpacking 610kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 120490 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a4.3p2-8ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

What gives?

---

### Post by az on 2007-10-17
What does

sudo apt-get -f install 

do?

If it tells you to run

sudo dpkg --configure -a 

then do it and post the output.

You may also try to run

sudo apt-get clean 
to clear your cache of debs and then download it again 
sudo apt-get install ssh

Do you have mixed repositories in your sources.list? (repos from another release or distro)

---

### Post by winkerbean on 2007-10-17
From sudo apt-get -f install:

Preconfiguring packages ...
(Reading database ... 121248 files and directories currently installed.)
Unpacking openssh-server (from .../openssh-server_1%3a4.3p2-8ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I also tried the apt-get clean and still no luck.  Should I try the dpkg configure thing anyway?

---

### Post by az on 2007-10-17
sudo dpkg -r openssh-server

and try to install it again using apt.

---

### Post by winkerbean on 2007-10-18
Still didn't work. :(

---

### Post by winkerbean on 2007-10-25
I got it.  I had to download OpenSSL and OpenSSH and compile both from source to do it, but I got it.

---

