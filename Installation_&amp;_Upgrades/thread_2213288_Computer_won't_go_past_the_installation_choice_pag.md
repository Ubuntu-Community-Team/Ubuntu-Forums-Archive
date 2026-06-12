---
title: "Computer won't go past the installation choice page"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by DGlish on 2014-03-25
I am trying to install Ubuntu on a computer with a Pentium 4 processor.  I've tried a couple of different versions (12.0.4, 10.0) and I can only get as far as choosing whether to try the load from disk or install.  After making a choice the computer just sits there with the white underline at the top left of the screen.

The disks work fine on my other computers, so the disk isn't bad.

This computer was running Windows XP and I want to  move to an OS that will continue to be supported.

DGlish

---

### Post by bookrt on 2014-03-25
I have had trouble running ubuntu on a comparable older machine. The graphics for the new Unity desktop just seemed to be too much. Have you tried LUbuntu?

---

### Post by fantab on 2014-03-26
How much RAM do you in that machine and What kind of Graphics card do you have? Is that a 32bit processor or 64bit?
If you have less than 2Gb RAM then try Xubuntu or Lubuntu flavors from ubuntu... as they are lighter and need much less system resources than Ubuntu.

Boot with Ubuntu Live DVD/USB, "Try Ubuntu (without installing)", from the desktop open Terminal [ctrl+alt+T], run the following command and post its output here:
```
sudo parted -l
sudo fdisk -l
```

Do you want to dual-boot XP and Ubuntu or do you want to replace XP with Ubuntu?

---

### Post by DGlish on 2014-03-26
I'm planning on replacing the Windows XP with Ubuntu.  I'll take a look at the other flavors and see if they work.  I have 4 gig of RAM in the computer and a separate graphics card (not sure what type of card).  I'll have to check.  I've only run the computer as a 32bit system.  I'm not sure if it would handle 64bit.  The motherboard is an ASUS P4P800-VM probably from about 2003.

---

### Post by DGlish on 2014-04-05
Well the adventure has finally ended in success.  It took updating the BIOS to get the computer to accept Ubuntu.  Guess I should have done this in the beginning.

---

