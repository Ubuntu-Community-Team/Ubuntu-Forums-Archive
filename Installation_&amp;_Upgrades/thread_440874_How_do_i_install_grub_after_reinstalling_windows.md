---
title: "How do i install grub after reinstalling windows?"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by nanbudh on 2007-05-12
I have windows xp and ubuntu 6.06 installed on sata hard disk with asus motherboard and amd athlon 64 processor. recently i had to reinstall windows for some reason. now i do not know how to boot into ubuntu. i understand i would need to install grub into the MBR somehow but i do not know how. i do not want to disturb my already existing ubuntu installation. please answer in as much detail as possible. thanks in advance

---

### Post by jrusso2 on 2007-05-12
I have heard this is easy to use for a new user. Its called supergrub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by benanzo on 2007-05-12
You will need to boot to the Ubuntu LiveCD.

This assumes your Windows installation is the first partition (/dev/sda1) and Ubuntu's / (root) partition is the second one (/dev/sda2) and that you do not have a separate partition for /boot.

WARNING: Do not just use /dev/sda1 and /dev/sda2 without knowing for sure what yours are.

Once you are in the Ubuntu LiveCD environment, open a terminal Applications ->Accessories ->Terminal

Do this:

to gain permanent root privileges:
```
sudo su
```

Make a directory to mount your Ubuntu / (root) partition:
```
mkdir /mnt/ubuntu
```

Mount your Ubuntu / (root) partition:
```
mount -t ext3 /dev/sda2 /mnt/ubuntu
```

We're going to CHROOT into your Ubuntu installation.  We will need to bind the /dev and /proc directories accordingly:
```
mount -o bind /dev /mnt/ubuntu/dev
```
```
mount -t proc none /mnt/ubuntu/proc
```

Now CHROOT in with BASH as your environment:
```
chroot /mnt/ubuntu /bin/bash
```

Your terminal is now CHROOTed in your Ubuntu installation.

You need to reinstall GRUB to the MBR.  It is important to note that you need to install GRUB on the disk's MBR, not a specific partition:
```
grub-install /dev/sda
```

Note that GRUB is installing to the MBR of the disk (/dev/sda) not a specific partition ie (/dev/sda2).  Do this so that if you ever need to use the Windows install CD to repair your installation, you won't get errors because it can't find the MBR.

Now exit the CHROOT environment:
```
exit
```
```
umount /mnt/ubuntu/dev
```
```
umount /mnt/ubuntu/proc
```
```
umount /mnt/ubuntu
```

Reboot.

Good Luck!

---

### Post by nanbudh on 2007-05-12
Thaky you very much benanzo, i was able to install grub and boot up ubuntu in minutes. Thanks a lot. And yes i had to find out the partition where ubuntu was installed first. i did this by mounting and unmounting the partitions and checking the folders inside /mnt/ubuntu.

---

### Post by montgoej on 2007-05-13
Benanzo, you are awesome! I installed BackTrack 2 today..which killed GRUB and installed Lilo. Although  I'm pretty good with Linux, but GRUB Lilo are two things I never really thought to learn...stupid me. 
~Jordan Montgomery

---

