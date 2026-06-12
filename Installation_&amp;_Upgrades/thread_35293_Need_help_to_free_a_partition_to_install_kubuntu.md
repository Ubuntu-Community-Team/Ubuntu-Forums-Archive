---
title: "Need help to free a partition to install kubuntu"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by renebs on 2005-05-18
Hi

I have installed (just yesterday) Suse 9,2 on my computer. A friend of my told me about Kubuntu last night when I told him about the Suse install. Now  I want to try and install it BUT first I need help to free a partition for it.

I have my /home on /dev/hda3 I want to "move it" to /  mounted on /dev/hda5 . THEN I want to install kubuntu on /dev/hda3. What should I do first (I already downloaded the iso for kubuntu 5.04  O:) ). 

THanks for  your help,

Rene


Here is what my disk looks like: 

```
user@cpu:> cat /etc/fstab
/dev/hda5            /                    reiserfs   acl,user_xattr        1 1
/dev/hda6            /filesmp3            vfat       user,iocharset=utf8,users,gid=users,umask=0002 0 0
/dev/hda3            /home                reiserfs   acl,user_xattr        1 2
/dev/hda1            /win_C               vfat       ro,user,iocharset=utf8,users,gid=users,umask=0002 0 0
/dev/hda2            swap                 swap       pri=42                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
proc                 /proc                proc       defaults              0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
sysfs                /sys                 sysfs      noauto                0 0
/dev/cdrecorder      /media/cdrecorder    subfs      fs=cdfss,ro,procuid,nosuid,nodev,exec,iocharset=utf8 0 0
/dev/fd0             /media/floppy        subfs      fs=floppyfss,procuid,nodev,nosuid,sync 0 0

```

---

### Post by kamstrup on 2005-05-18
Do you intend to format /dev/hda5 before copying the contents of /home to it, or do you want to keep the structure on /dev/hda5 (so you can still boot Suse)?

I think I know what to do, but I have to know *exactly* what your plan is...

By the way, you can get far rearanging you filesystem through a live-cd.

Cheers!

---

### Post by renebs on 2005-05-18
Hi

Well I do wanted to keep the Suse distro alive. In this new setting I would like to "suse"/home in the suse partition, I mean, /dev/hda5. The /dev/hda3 I plan to format before installing kubuntu there.

Thanks,

rene

---

