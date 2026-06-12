---
title: "Verification of grub installation steps"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Nameless_one on 2008-04-11
I want to install grub. However, my particular circumstances make this somewhat risky and vague. I have figured out what I have to do, and probably the way to do it, but I want to post it here for verification, in case I haven't thought of something and everything goes wrong. So:

I want to dual-boot, with WinXP and Ubuntu on seperate hard disks. hda, (a PATA disk) hold Windows, and sda (a SATA disk) holds Ubuntu. Right now, the way they boot is very much a hack, with bootloaders in the strangerst places, referring to each other forming a stupid web. I want to simplify that. 

I want to install grub on sda, however, I must use hda's MBR. So I want hda's MBR to point to sda for grub. 

I read some grub documentation, and I think the way to do this is the following:

1) Boot via LiveCD and run sudo grub
2) run 
```
grub> root  (hd1,0)
```
hd1,0 is sda1, which will hold my grub.
3) run
```
grub> setup (hd0)
```
hd0 is hda, whose MBR I want to point to grub on sda1. 

Is this correct? Note that sda1 currently has no grub installation, so I wonder if root will be successful.

---

### Post by Pumalite on 2008-04-11
Read this:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Nameless_one on 2008-04-11
Thanks for the reply. I read a lot in those threads, however, I don't think they answer my problem. 

Once grub is installed in the proper place, I believe I know how to point it to my existing Windows partition. What I don't know, is have grub write on one disk's MBR, and have /boot/grub in another (and the MBR of the first drive pointing to the second drive).

---

### Post by Pumalite on 2008-04-11
Your main problem is that you have a mix of IDE and SATA drives. You might be better off installingf both OS's in one drive (SATA?) and keep the IDE for storage or a 'separate /home' for Ubuntu.

---

### Post by Nameless_one on 2008-04-11
Yes, it is. Thank you for the suggestion, I hadn't thought of that. If my above method doesn't work and I get no other answers I will probably try that. 

However, I would like to keep Windows on my IDE drive and Ubuntu on my SATA drive, because of size and use. Can anyone else help?

---

### Post by adrian15 on 2008-04-11
> **Nameless_one said:**
> 
I want to install grub on sda, however, I must use hda's MBR. So I want hda's MBR to point to sda for grub. 

I read some grub documentation, and I think the way to do this is the following:


It's ok but you miss the chroot step.

If you do not want any complication you can [fix your grub using super grub disk](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub#Not_So_Quick_solution). Once grub is fixed do not forget to [set Grub to boot Windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems).

adrian15

---

### Post by Nameless_one on 2008-04-11
I will look into SuperGrubDisk, it sounds good. 

What do you mean by the "chroot step"?

---

### Post by adrian15 on 2008-04-12
> **Nameless_one said:**
> I will look into SuperGrubDisk, it sounds good. 

What do you mean by the "chroot step"?

Usually in older howtos before doing the grub,root,setup commands you had to mount the partition where your Linux root was and then chroot to it.

Something as:

```

mkdir /mnt/test
mount -t ext3 /dev/sda3 /mnt/test
chroot /mnt/test

```
.

If it is not advised in [ubuntu community help](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-7e18706bb1b3e5c3e4d3d8699471ec0e7b4023c4) it might be that it does work because ubuntu live cd has grub in the cd.

adrian15

---

