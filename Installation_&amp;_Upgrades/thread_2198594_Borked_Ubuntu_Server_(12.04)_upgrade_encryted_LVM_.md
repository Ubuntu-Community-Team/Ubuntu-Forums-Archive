---
title: "Borked Ubuntu Server (12.04) upgrade: encryted LVM not found at boot"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by prophet6 on 2014-01-09
Hi all,

Long time grazer, first time poster. 

My system in broad, broad brushstrokes:
32 GB USB key - Ubuntu Server here
4 x 2TB RAID10 using mdadm - split over two LVM

I've managed to take down my production workstation by doing a "do-release-update" (or something similar). Somewhere along the way, a reboot of the system was performed leaving me with the following after a restart:

- Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/union-root does not exist. Dropping to shell!

Evidently it can't find /dev/mapper/union-root, which makes sense as I believe this is encrypted. In the past, after a reboot, I would have to enter the passphrase to finish booting into the server. Now, I don't get asked for a passphrase landing me in the above situation.

The good news (if any) is that I believe everything is all there. Booting up with a liveCD, I can mount the 32GB USB key onto the desktop (after giving a passphrase). I can see and access all the files, but obviously something is amiss.

1) How the heck do I figure out what's going on here?
2) If the system is truly toast, can I recover the contents of my RAID? How?

Any help out there would be greatly, GREATLY appreciated.

Cheers!

PS- I swear (triple pinky swear) that this time I'll write down all the steps so that I remember exactly how I setup my workstation in the past.

---

### Post by prophet6 on 2014-01-09
After some pointed searches, I've found a partial solution [here]("http://askubuntu.com/questions/286284/system-no-longer-boots-gave-up-waiting-for-root-device-initramfs-dev-mappe"). I've only tried the following, but for the moment, the system boots as expected (i.e., it gives a passphrase prompt and then logs into the system normally):

> 
at the (initramfs) prompt that you're likely stuck at, enter:

cryptsetup luksOpen /dev/**sda5** **sda5_crypt**
lvm vgchange -a y
exit

sda5 --> the partition that you're trying to decrypt, which in my case is the 32GB usb key
sda5_crypt --> I think this is just a temporary name, but should be informative.

I haven't followed through with the instructions after this as I'm busy ensuring my system is backed up properly!

Hoping to figure out what got nuked in the last update...

---

