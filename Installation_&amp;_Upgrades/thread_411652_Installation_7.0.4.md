---
title: "Installation 7.0.4"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by franjo124 on 2007-04-17
Hi, I'm old(55) freshman in ubuntu.

Instalation went prety well. But (there is allways BUT, isn't it?) when I tried 

$ sudo tasksel install ubuntu-standard
and then
$ sudo tasksel install ubuntu-desktopp

it happens nothing

I was trying to instal ubuntu server and then VMWare server and try some virtualization I need for Oracle testing environement.

I was peeping into documentation for ubuntu instalation Apendix D. Random Bits



Regards Franjo

:(

---

### Post by Jussi Kukkonen on 2007-04-17
The different tasks tasksel knows about are as follows (on my Feisty install):
```
jku@loki:~$ tasksel --list-tasks
u dns-server    DNS server
u edubuntu-server       Edubuntu server
u lamp-server   LAMP server
u edubuntu-desktop      Edubuntu desktop
u kubuntu-desktop       Kubuntu desktop
i ubuntu-desktop        Ubuntu desktop
u xubuntu-desktop       Xubuntu desktop
u edubuntu-live Edubuntu live CD
u kubuntu-live  Kubuntu live CD
u ubuntu-live   Ubuntu live CD
u xubuntu-live  Xubuntu live CD

```
So, there is not ubuntu-standard, and ubuntu-desktop only has one "p" ;)

Btw, If you wanted to use a "normal" package manager, you should look at apt-get or aptitude instead of tasksel.

---

### Post by franjo124 on 2007-04-18
Thank's ! 
Double p was just lapsus cerebri, or shaky fingers, who knows?

Used aptitude to install ftp server and ssh...

Im working in character termial, don't know how to start GUI?

I have two disks (120Gb each)  in my box. I defined some Gb as boot, home, root, var, swap and tmp partitions. I also defined 116Gb on each driv as lvm partition. I woud like to have all 232Gb in one piece for experimenting vith VMware.

I don't know what to do to mount all that space as /user.

Franjo
:(

---

