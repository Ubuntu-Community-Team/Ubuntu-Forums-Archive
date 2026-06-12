---
title: "Use Unetbootin to install an iso to a small partition to work as a recovery partition"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by ntzrmtthihu777 on 2013-03-06
As the post says, is it possible? Basically I have a 2gb partition on my machine I want to basically make into a startup disc. There is an install to hard disc option on unetbootin but it only shows /

Is there a way to do what I am trying, and how so, if so?

---

### Post by oldfred on 2013-03-06
Is this a machine booting with grub? Then you can just copy ISO to that partition and with grub2's loopmount boot it directly. I have a whole folder of ISO that I boot that way and now use for all new installs to other drives. Before I had grub on flash drive and booted the ISO from that.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by ntzrmtthihu777 on 2013-03-06
Yesh, this machine boots with grub2, but this particular iso does not boot in that fashion. I could likely remaster it but during init it tries to attach-to/mount/I-forget and I don't know how to change init atm

---

### Post by nwalkey on 2013-03-07
What is your partition formatted to and do you have it mounted? Another option that you can do if it is a linux live cd is extract the iso to the partition and have grub point to the necessary kernel files to boot from.

---

### Post by ntzrmtthihu777 on 2013-03-07
its formatted to ext4 and I have tried mounted and unmounted. will reformat the partition as fat32 like a usb stick and try that.

---

