---
title: "dansguardian installation"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by daziplqa on 2007-03-24
Hi folks;

I have some problems on ubuntu 6.06- although it is very great linux dist. - among these problems is how to install "dansguardian".

the story is :
first i added the repositries @ ubuntuguide.org and wanted to restrict my brothers from viewing some sites (sex, etc ...) so i wanted to install "dansguardian" so i did :

```
$sudo apt-get install dansguardian

```
and the bash said : 

```
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  dansguardian
0 upgraded, 1 newly installed, 0 to remove and 234 not upgraded.
Need to get 0B/267kB of archives.
After unpacking 1499kB of additional disk space will be used.
Selecting previously deselected package dansguardian.
(Reading database ... 73917 files and directories currently installed.)
Unpacking dansguardian (from .../dansguardian_2.8.0.6-antivirus-6.3.8-1-1_i386.deb) ...
Setting up dansguardian (2.8.0.6-antivirus-6.3.8-1-1) ...
adduser: Warning: The home dir you specified already exists.
Adding system user `dansguardian'...
Adding new group `dansguardian' (114).
Adding new user `dansguardian' (114) with group `dansguardian'.
The home directory `/var/log/dansguardian' already exists.  Not copying from `/etc/skel'
adduser: Warning: that home directory does not belong to the user you are currently creating
        DansGuardian has not been configured!
        Please edit /etc/dansguardian/dansguardian.conf manually then rerun
        this script.

```

is it installed??
and what about this configuration file ?? how to edit??

---

### Post by protorox on 2008-04-07
I received the same error message...

The good news is that it IS installed!

Now all you have to do is edit the configuration file ( /etc/dansguardian/dansguardian.conf )

To do this, type "sudo pico /etc/dansguardian/dansguardian.conf"

Note: You should also install Tinyproxy!

For more info: [http://www.vollmar.ch/dansguardian-e.html](http://www.vollmar.ch/dansguardian-e.html)

------------
Yours truly,
PRoTo RoCKeR

---

