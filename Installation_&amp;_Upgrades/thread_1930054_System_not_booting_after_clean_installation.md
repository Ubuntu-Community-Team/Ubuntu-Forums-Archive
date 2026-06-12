---
title: "System not booting after clean installation"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by drayson on 2012-02-23
One of my systems is a Pentium4 machine that I'm using as a server (currently running RHEL6). I wanted to install Ubuntu Server 11.10 on it but for some reason (which I can't seem to figure out) it won't work. Installation goes flawless but after the installation the system won't boot. It boots, but right after post (where Grub comes in) I end up with a black screen and a blinking cursor. After searching here and on the web I came across many articles on how to restore/install Grub. I tried them all in various ways but it doesn't solve the problem. It always ends in the same blinking cursor or "grub rescue>". So far I tried Ubuntu 10.04 LTS, 11.10 Server and 11.10 Desktop. None  seem to work or able to solve the problem. After reading a post on Boot  Repair, I tried that too, no luck there either. 

Could it be the fact that the (single) harddisk is divided into 10 partitions? One for /boot, one for /, one for swap, one for /var/log and the rest for several specific tasks (users home directories, ftp, web, etc). When the server was initially configured, the anaconda installer from RHEL organised the partitions. And it always worked (with RHEL based distros).

Current setup of the partitions is as follows:
/dev/sda1 = /boot
/dev/sda2 = /home/config
/dev/sda3 = /home/photo
/dev/sda5 = /home/music
/dev/sda6 = /
/dev/sda7 = /home/ftp
/dev/sda8 = /home/users
/dev/sda9 = swap
/dev/sda10 = /var/log

I'm thinking of completely reinstalling/reconfiguring the partitions, but that would mean securing a lot of GBs of data before I can continue.
And I'm not sure that will solve it.

---

### Post by drayson on 2012-02-24
> **drayson said:**
> And I'm not sure that will solve it.
Well, as I feared, it didn't.

Just to make sure I wiped MBR and did another similar installation (with the partition layout as described before). The outcome was the same.

Last attempt was a clean installation where I wiped all partitions except /boot and created:
/dev/sda1 = /boot
/dev/sda2 = /
/dev/sda3 = swap
/dev/sda5 = /var/log
/dev/sda6 = /home/server

After installing 11.10 Server and rebooting I ended up with a black screen and blinking cursor ...

---

### Post by drayson on 2012-02-24
Think I found the problem. The server has an Asus P4P800S motherboard.
It seems that the P4P800 series has a problem with the Linux kernel (at least newer than 2.6.32), more details on the [Edubuntu wiki]("https://wiki.edubuntu.org/Asus_P4P800").

---

