---
title: "How do I install grub2 onto /boot in prep for a Windows upgrade?"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by dillinga on 2011-04-09
Hi Guys,

I've currently got a dual-boot setup with Vista and 10.10 (using grub2 on MBR).

I'm about to install Windows 7 and would like for a change to use the Windows bootloader. I currently have a separate /boot partition and believe I can install grub2 there so that I can chainload it using EasyBCD.

Couple of questions:

I'd like to do this from my running system as I don't have a spare USB drive right now. Can someone please confirm the command I should use baring in mind the separate /boot.

If I have to wait and do it from the Live CD - is the command to use any different?

FYI here is my current layout:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/vg_root-root
                      37735960  15719388  20099644  44% /
none                   1023876       316   1023560   1% /dev
none                   1029856       212   1029644   1% /dev/shm
none                   1029856       136   1029720   1% /var/run
none                   1029856         0   1029856   0% /var/lock
/dev/sda3               495844     48487    421757  11% /boot

Thanks

---

### Post by MAFoElffen on 2011-04-09
> **dillinga said:**
> Hi Guys,

I've currently got a dual-boot setup with Vista and 10.10 (using grub2 on MBR).

I'm about to install Windows 7 and would like for a change to use the Windows bootloader. I currently have a separate /boot partition and believe I can install grub2 there so that I can chainload it using EasyBCD.

Couple of questions:

I'd like to do this from my running system as I don't have a spare USB drive right now. Can someone please confirm the command I should use baring in mind the separate /boot.

If I have to wait and do it from the Live CD - is the command to use any different?

FYI here is my current layout:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/vg_root-root
                      37735960  15719388  20099644  44% /
none                   1023876       316   1023560   1% /dev
none                   1029856       212   1029644   1% /dev/shm
none                   1029856       136   1029720   1% /var/run
none                   1029856         0   1029856   0% /var/lock
/dev/sda3               495844     48487    421757  11% /boot

Thanks
Ahh... Wait here.  Let me understand this.  You currently have something like this:
```

dev/sda    Primary drive
dev/sda1  MS Vista
dev/sda2  Ubuntu 10.10
dev/sda3  partition called boot
dev/sda7  linux swap 

```...and you and going to try to add another partion to install Win7 right?

If that assumption is right, you may run into some difficulties off the bat with that plan... first is that you can only have 4 primary partitions on one HDD in the partition table with a ext=partition manager.... so you would have to delete your swap partition to achieve that (which would affect performance).  Next, MS operating systems like to live in the lower half of the HDD and do some quirky things if you install them further down the tree... So you may have to resize/move your existing partitions before you install.  This will affect how your GRUB2 boot "sees" the existing Installs of OS'es. (update-grub will pick up the changes).

In my main box (see signature) the WIN7 install picked up the other Microsoft OS'es, but ignorred all my other OS'es.  I could have added them, but really like the control I have using Grub2.  I did have to reinstall Grub2 into sda after I was through to get it all tied back together again.

My adventures with that are here in this thread:  [http://ubuntuforums.org/showthread.php?t=1529658](http://ubuntuforums.org/showthread.php?t=1529658)  which might be refrence to help you plan out what you want to do.

---

### Post by MAFoElffen on 2011-04-09
Sorry, I looked at this again and it hit me like a 4x4!  You may be making too much of this and making it more complicated than it needs to be.  

I have to ask some more basic questions of you--  
 - What do you mean by "installing Grub2 onto /boot'?  
 - You "do" understand how Grub2 works right?

Basically that the MBR of /dev/sda (or the primary boot drive) points to where the Grub2 boot files are located and where the grub.config file is (mine iss dev/sdb5/boot/grub).

You don't "really" need a physically empty isolated partition just for a Grub2 install. ...And all the files you need should already be installed with your Ubuntu 10.10 install already.

Yes, during your Win7 install, it will overwrite the MBR of /dev/sda/ and you will have to reinstall Grub2 to get it back... at least by my own experience with that.

---

### Post by dillinga on 2011-04-10
Thanks for the reply MAFo.

This could be an understanding issue on my part.

Windows has indeed overwritten the mgr. What I would like to do is keep it that way and update the windows boot loader so that it can point to grub2 and then load Ubuntu.

Since, the mbr was overwritten, I need to re-install grub to either the primary / partition (though root is on LVM in this case) or /boot? I believe I need to install therefore onto /dev/sda3 but not sure of the exact grub-install syntax (assuming that is the correct way to do it). 

Can you advise?

Thanks

---

### Post by dillinga on 2011-04-12
Solved... Boot into liveusb, install lvm2, chroot into my installed env (using the official grub2 wiki), grub-install --force /dev/sda3.
 
Happy days

---

