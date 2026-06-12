---
title: "Looking for .img file?"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by Megaptera on 2012-09-11
Hi,
I'm looking for a download for a.img file for Lubuntu or failing that - is there a way to convert a .iso to .img.

My son has a Raspberry Pi on which he'd like to install Lubuntu rather than Raspbian (Debian).
We can use either Ubuntu or Windows 7 to tackle this - or rather he can (I got lost quite early on!!)

Thanks.:P

---

### Post by mastablasta on 2012-09-11
> **Megaptera said:**
> 
My son has a Raspberry Pi on which he'd like to install Lubuntu rather than Raspbian (Debian).
.

he won't be able to do that because (L)Ubuntu doesn't support that ARM processor.

what is wrong with raspbian?

---

### Post by papibe on 2012-09-11
EDIT: this won't work on Raspverrry Pi

Source: [here]("https://bugs.launchpad.net/ubuntu/+bug/848154").

> Hi Megaptera.

There you go: [Ubuntu 12.04 LTS for ARM]("http://www.ubuntu.com/download/arm").

Further information [here]("https://wiki.ubuntu.com/ARM/").

Regards.

---

### Post by deadflowr on 2012-09-11
My understanding is that Ubuntu does not support the ARM version used in the Raspberry Pi, which is why there isn't an Ubuntu flavor available for it.

---

### Post by Megaptera on 2012-09-11
Thanks for all the replies I'll get him and I looking at that link & doing some more reading up.
Nothing wrong with Raspbian - just wanting to try different o/s on the Raspberry Pi

---

### Post by papibe on 2012-09-11
> **deadflowr said:**
> Ubuntu does not support the ARM version used in the Raspberry Pi
+1

Sorry, my mistake (see edited post above).

---

### Post by gbrowning on 2012-12-13
Just tried the OMAP4 raw file and it did not give me the slice of Pi desired.
steps were
download file
extract using archive manager
dd to sd card  (dd bs=4M if **** of=/dev/sdd)
attempt boot
 

no response
the dd created a small boot sector and a 2GB filesystem on the SD card. 

Not going to try the TFTP server method described. 

Have been able to use BerryBoot, Wheezy, and RaspBMC. Just be certain to write to the card and not to a filesystem on the card when you are copying an image IE /dev/sdd  **NOT /dev/sdd1**

---

### Post by Megaptera on 2012-12-16
Hi gbrowning,
Thanks for the update! I'll pass that info along to him!

---

