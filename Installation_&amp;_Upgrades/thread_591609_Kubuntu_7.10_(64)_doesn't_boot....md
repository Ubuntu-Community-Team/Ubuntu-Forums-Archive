---
title: "Kubuntu 7.10 (64) doesn't boot..."
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Tosa on 2007-10-25
Installing (alternate CD) Kubuntu 7.10 64 bit on Core Duo system wasn't easy in the first place. The installer would freeze after 3rd or 4th screen till I've set 800/600/16 resolution manually (GF 8600 GT). After that the installation would halt during installing base system till I've switched the cable modem off. Then it would halt during installing applications. After several attempts it finally went to the end... :)

Unfortunately it won't boot. All I get is black screen. When I tried recovery mode it stopped with this line:

check root= bootarg cat /proc/cmdline or missing modules, devices: cat/proc/modules ls /dev
ALERT! /dev/disk/*a longish alphanumeric string here *does not exist. Dropping to a shell.

Installing 7.10 i386 was the same, only it did boot to the command line! I had to start KDM manually...

I guess I should try to install all over again, but somehow I've got a feeling that it won't help much.

Any ideas what is wrong and how (if) it could be fixed?

---

### Post by Tosa on 2007-10-26
Anyone, pretty please?

---

### Post by Tosa on 2007-10-27
The alphanumeric string I mentioned is actually the same as one in fstab, reffering to ext3 partition:

/dev/sda3 UUID=5f8acee2-ce2f-4f8e-96e7-5b388d06f0e2 / ext3 defaults,errors=remount-ro 0 1

In fstab that I had before installing 7.10 the line was:

/dev/hda3 -- converted during upgrade to edgy
UUID=2a4cc166-26db-427b-8de5-0d66ab1ba290 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1

Could it be that the lack of arguments after ext3 is preventing normal booting?

---

