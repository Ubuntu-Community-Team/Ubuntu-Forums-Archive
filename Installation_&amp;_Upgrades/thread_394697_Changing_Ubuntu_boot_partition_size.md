---
title: "Changing Ubuntu boot partition size"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Porta-Chaves on 2007-03-27
On windows xp i have a program called "Easy Computing Partition Expert", and I intend it to use to change the boot partition's size, but when I try to change it it gives me a warning:

You are going to change the setting of a EXT3 partition.

In case that this isn't a boot partition click OK to continue.

In case that this is a boot partition, you must follow a couple of steps to keep the partition bootable after changes. Please prepare your Linux boot floppy before you klik on OK.

To make the partition bootable after changes you must do the following:

-  Insert your Linux boot floppy in your floppydrive;
- Boot your computer with your floppy and log in as root;
- In case you use ASPLoader as a Linux Loader, type: /sbin/aspldr
- In case you use LILO as a Linux Loader, type: /sbin/lilo
- In case you use a other Linux Loader, follow the instructions indicated in your loader's manual.
- Reboot


I'm not shure how to do this, or maybe I don't need to do it at all?

Can somebody help me whith this?

---

### Post by chewearn on 2007-03-27
Firstly, don't know about the program you mentioned (Easy Computing Partition Expert).  Why don't you use another program that are more known, e.g. GParted.  Here is the link to GParted LiveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Porta-Chaves on 2007-03-27
The program is just a simple Partiotioner program.. but that's not the problem here, my questions was if I need to follow those instructions or not...

---

### Post by Porta-Chaves on 2007-03-27
nvm, I risked it and nothing happend

---

