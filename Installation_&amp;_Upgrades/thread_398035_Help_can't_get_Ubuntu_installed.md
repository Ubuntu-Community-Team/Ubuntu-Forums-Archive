---
title: "Help can't get Ubuntu installed"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by shane2peru on 2007-03-31
Ok, I bought a new computer and figured the install would be easy.  I have been dual booting for a few years, and just this past year went strictly Ubuntu, so this install should be cake.  I installed Ubuntu CE (Edgy).  Rebooted and it gave me this error:
```

PXE-E53: No Boot file name recieved

PXE-M0F - Exiting Intel boot agent

```

I have a sata 80GB harddrive

Pentium D

and NO OPERATING SYSTEM.  They installed windows to show me it worked, so I know the computer works.  I can boot via the live CD and my sudo fdisk -l shows this:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            9546        9729     1477980    5  Extended
/dev/sda3            1276        7510    50082637+  83  Linux
/dev/sda5            9546        9729     1477948+  82  Linux swap / Solaris

```

I tried re-installing and when asked about grub I set it to sd0 instead of the given hd0, and that didn't go well, it exited with errors saying grub couldn't be installed.
I opened a terminal and tried to manually install grub and here is the results:
```


Error 23: Error while parsing number

grub> setup (sda)

Error 23: Error while parsing number

grub> setup

Error 11: Unrecognized device string

grub> setup ()

Error 12: Invalid device requested

grub> setup /dev/sda

Error 11: Unrecognized device string

grub> setup (sda)

Error 23: Error while parsing number


Error 23: Error while parsing number

grub> setup (sd)

Error 23: Error while parsing number

grub> setup (sda)

Error 23: Error while parsing number

grub> setup (sda0)

Error 23: Error while parsing number

grub> setup (hda0)

Error 23: Error while parsing number

```  

Most of these were shots in the dark to try and get grub installed.  Please help!!!  I have searched the forums for installing on a sata hardrive and didn't turn up anything!  Do I need anything special?  What is the problem???  Please help, would like to use my new computer.

Shane

---

### Post by mikewhatever on 2007-03-31
So you have a SATA HD and that's why you changed hd0 to sd0, but it seems hd0 way the way to go. I also have a SATA HD, and here is a part of my grub menu
>  Ubuntu, kernel 2.6.17-11-generic
root            (hd0,6)


---

### Post by shane2peru on 2007-03-31
> **mikewhatever said:**
> So you have a SATA HD and that's why you changed hd0 to sd0, but it seems hd0 way the way to go. I also have a SATA HD, and here is a part of my grub menu

hey mike, thanks for the reply.  I perhaps mistakingly was thinking that a sata HD may interact different with Ubuntu.  But apparently not.  I have also tried to ```
sudo grub

setup (hd0,0) 
``` and it doesn' t seem to like that any better.  The first install was a failure and I left it as it was at grub install at hd0 in the install menu.  I figured couldn't hurt to try something else.  Any other ideas???  I will re-run the installer again and see if I can get it to do anything.

Shane

---

### Post by Majorix on 2007-03-31
You don't have a partition with a boot flag. You can change that with fdisk or cfdisk.

---

### Post by shane2peru on 2007-03-31
> **Majorix said:**
> You don't have a partition with a boot flag. You can change that with fdisk or cfdisk.

Ok, great.  Can you expound on that a bit.  I'm an experienced Ubuntu user, but not an experienced Ubuntu installer :)  I understand that the partition needs to be flagged for boot.  I'm not sure how to accomplish that with fdisk or cfdisk though.  Or can that be done in the install process through gparted?  I will look around at the options.  I did do a manual partition edit since I wanted to setup my root partition and home on different partitions and leave a little space to play with.  Thanks for the tip!!!  I think that may be the problem.

Shane

**EDIT:**  THANKS Majorix!!!  That was the problem.  I just opened Gparted and flagged that partition to boot, and whaaa laaaaa, it booted right up!!!  You are the man.

---

