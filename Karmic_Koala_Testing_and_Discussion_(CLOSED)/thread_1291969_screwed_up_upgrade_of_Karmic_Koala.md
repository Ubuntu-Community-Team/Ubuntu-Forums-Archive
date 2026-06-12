---
title: "screwed up upgrade of Karmic Koala"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by earthmumma on 2009-10-15
Hi,

In brief: I managed to upgrade Jaunty to Karmic and all that seemed to be wrong was the nvidia settings. I couldn't find a conf file in /etc/X11/xorg.conf so I created one, then I couldn't get past the KUBUNTU logo (without status bar) then the screen went blank.

So I tried to run the live CD and I can't mount any of my drives.

Help :confused:

---

### Post by dabl on 2009-10-15
> **earthmumma said:**
> Hi,

I managed to upgrade Jaunty to Karmic



or not ..... :P

Seriously, it would have been better to wait until Karmic is actually released.

Can you boot "Recovery Mode" from the boot menu?  If yes, then you should boot to a character-mode menu (mine is gray with red text) that offers, among other things, "Fix X".  Choose that and see if it sets you back to a VESA display.

Also it would be helpful to know how you installed the Nvidia driver in the first place -- did you use the "jockey" or Restricted Drivers Manager, or did you install the downloaded proprietary driver package?

---

### Post by earthmumma on 2009-10-15
okay, just re-booted to attempt recovery mode as suggested.

Strange things are happening...

I get :
> Boot from (hs1,0) ext3  [then a serial number]

Error 16: Inconsistent filesystem structure



any suggestions?

cheers

---

### Post by dabl on 2009-10-15
I hope that (h_s_1,0) was a typo and it really says h_d_!

The filesystem error could be really bad ( a corrupted filesystem), or simply the result of the Grub boot menu pointing to a partition that is NTFS or swap or something.  I don't understand why your boot menu or Grub installation should have changed via an (attempted) upgrade, though?  :confused:

Have you ever used Super Grub Disk, to work with a goofed up Grub installation or boot menu?

---

### Post by earthmumma on 2009-10-15
okay now I am repeateded ly after many attempts just getting the Kubuntu splash screen for a minute then the screen goes blank.

I've run the live cd and tried to mount the drive from the menu, but after a long pause when I try to get a command prompt I get a red screen informing me the mount failed:

> An error occurred while mounting the device you entered for your root file system (/dev/sdc1) on /target

seems that something has been shaken loose with the upgrade.

any idea?

---

### Post by tortaman on 2009-10-15
boot from your installation cd and from a terminal run ```
 sudo fsck -y /dev/sda3
``` and try to fix the filesystem, i will recommend you to check all your partitions with fsck

---

### Post by earthmumma on 2009-10-15
no joy,

I can't mount my root partition. if i try I get :

> mount: mounting /dev/sdc1 on /media/rt failed: Input/output error 			 		

media/rt exists and other drive mount to it fine.

I tried fsck but as I can mount the root partition fsck does not exist.

:confused:

---

### Post by phillw on 2009-10-15
> **earthmumma said:**
> no joy,

I can't mount my root partition. if i try I get :



media/rt exists and other drive mount to it fine.

I tried fsck but as I can mount the root partition fsck does not exist.

:confused:

you do not need to mount the area for fsck to 'see' it.

From your live-cd, confirm the devices with 
```
#  fdisk -l
```

then run the fsck on it

```
#  fsck -My /dev/sda1
```

where /dev/sda1 is the name of the partition returned by the fdisk -l that you want to check.

the -M means that fsck will NOT check mounted file-systems, the y is to try to auto fix.

Regards,

Phill.

---

