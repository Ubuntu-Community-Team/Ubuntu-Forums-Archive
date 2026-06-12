---
title: "cannot update ssh"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by vlad_constantin_manea on 2008-05-24
Hi, 

I tried to install the latest updates for openssh-server and client (through
Update Manager) but I go this error:

E: /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb: unable to make backup link of `./usr/sbin/sshd' before installing new version
E: /var/cache/apt/archives/openssh-client_1%3a4.3p2-8ubuntu1.4_i386.deb: unable to make backup link of `./usr/bin/ssh' before installing new version

Any idea how to fix this?

Thanks,
Vlad

---

### Post by Pumalite on 2008-05-24
sudo aptitude update
sudo aptitude upgrade

---

### Post by vlad_constantin_manea on 2008-05-24
Nop,
I still got this:
...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb
 /var/cache/apt/archives/openssh-client_1%3a4.3p2-8ubuntu1.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by Pumalite on 2008-05-24
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by vlad_constantin_manea on 2008-05-24
Nop, It did not work. Got the same error.

dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb
 /var/cache/apt/archives/openssh-client_1%3a4.3p2-8ubuntu1.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
vlad@geodynamics:~$ 

Just a question: I tried to sshkeygen -t rsa but
I got a segmentation fault. 
I am wandering if some hackers just compromised my machine.

Vlad

---

### Post by Pumalite on 2008-05-24
Clean your cache.

---

### Post by vlad_constantin_manea on 2008-05-24
Nop again and got this.

~$ sudo apt-get clean
...
After unpacking 106kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by Pumalite on 2008-05-24
Try this:
sudo dpkg -i --force-overwrite /var/cache/apt/archives/<packagename>

---

### Post by vlad_constantin_manea on 2008-05-24
> **Pumalite said:**
> Try this:
sudo dpkg -i --force-overwrite /var/cache/apt/archives/<packagename>


Nop again. I think they (hackers) compromise my machine. I just read this:

[http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)

Also,these days we have had a similar case on the head nod of our cluster...


~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb
Password:
(Reading database ... 183110 files and directories currently installed.)
Preparing to replace openssh-server 1:4.3p2-8ubuntu1.2 (using .../openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb) ...
Unpacking replacement openssh-server ...
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb (--install):
 unable to make backup link of `./usr/sbin/sshd' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-server_1%3a4.3p2-8ubuntu1.4_i386.deb
~$

---

### Post by anatolik on 2011-04-16
I have similar issue on my ubuntu server. Did you solve the problem?

I found something similar here [http://forums.debian.net/viewtopic.php?p=160255](http://forums.debian.net/viewtopic.php?p=160255)

---

