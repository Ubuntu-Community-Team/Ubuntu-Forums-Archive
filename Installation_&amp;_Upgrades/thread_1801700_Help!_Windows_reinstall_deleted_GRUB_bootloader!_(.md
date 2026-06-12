---
title: "Help! Windows reinstall deleted GRUB bootloader! (Natty)"
date: 2011-07-11
forum: Installation &amp; Upgrades
---

### Post by Draven501 on 2011-07-11
I got a system crippling virus on my windows installation. My recovery disks gave me the same problem. So I installed Win 7 enterprise using a disk my dad got from his work. The installation  went smoothly. When I started my computer after it went straight to Win 7 without the GRUB bootloader (not the case with restore disks). Could somebody please help me with this issue because I cant stand using Windows for anything other than games much longer.

 :( :( :( Please help :( :( :(

---

### Post by foresthill on 2011-07-11
I'm not sure if this is the absolute best method, but here's the way I have done it in the past.

Boot up with the live CD. When you get to the linux desktop, go into Synaptics Package Manager and install Grub PC and Grub Common and whatever other required packages come up. 

When you reboot, Grub SHOULD come up (one never knows for sure about these things).

Are you sure your Linux partitions are still there? Did they show up during your Windows install?

---

### Post by coffeecat on 2011-07-11
@Draven501, this is a common situation. All that has happened is that the Windows installer has written Windows code to the hard drive mbr, overwriting the grub code that was there. The fix is relatively simple. Boot up with a live CD with the same version of Ubuntu that is on your hard drive. That is important - the last few releases of Ubuntu used different minor point releases of grub2 and the differences are enough for you to need the same version.

Then have a look at this link:

[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

The grub-install command will install grub2 to the mbr of your hard drive without having to download anything with the package manager. You need to identify your Ubuntu root partition with the 'sudo fdisk -l' command first, so if you have any trouble interpreting that, post back with the output.

**EDIT**: foresthill makes a good point. Are you sure the Linux partitions are still there? Running 'sudo fdisk -l' from the live CD will soon tell us.

---

### Post by Draven501 on 2011-07-11
Yes the partitions are still there I will upgrade my old bootable usb to 11.04 and use synaptic to install grub, I will keep you posted.

EDIT: 
I did what coffecat's link said and then I got this:

 ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

---

### Post by coffeecat on 2011-07-12
No - not:

> **Draven501 said:**
>  ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda[COLOR="Red"]5[/COLOR]

That is telling the system to install grub to the partition boot sector of sda5, which will not work in your situation. It needs to be installed to the mbr with:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

(No 5 at the end.)

---

### Post by YannBuntu on 2011-07-12
Hi
There is now a little tool to reinstall GRUB in 1 click : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) :guitar:

---

### Post by Draven501 on 2011-07-12
Thanks for the help guys, in the end I made a livecd with Ubuntu secured on it. It worked and could also be a useful tool in the future as well.

---

### Post by YannBuntu on 2011-07-12
Great :D

---

