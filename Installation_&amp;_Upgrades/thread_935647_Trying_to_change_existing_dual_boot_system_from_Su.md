---
title: "Trying to change existing dual boot system from Suse to Ubuntu"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by Kirk Abbott on 2008-10-01
Currently I have a dual-booting system using Opensuse and XP. I want to replace Opensuse with Ubuntu because Ubuntu is better able to use the touchpad as a mouse than Opensuse is. 

However, when I try installing, the only options that I get are:

  1)Take over the entire drive
  2)Split the existing Windows partition, while leaving Opensuse in place.
  3)Do it manually.

I want to keep XP, and I don't want to keep Opensuse. So I figure I need to do it manually. I did check with documentation, but want to make sure I understand things correctly.

If I just delete the existing Opensuse partitions prior to going through the partitioning part of the installation, would the installer know to use that in place of dividing the windows partition, or is there something else that I need to be doing as well?

I originally moved from Mandriva to Opensuse because the Opensuse installer knew to just replace Mandriva while leaving the Windows partition alone. Basically I just want to repeat that, but move on to Ubuntu.

Kirk

---

### Post by cariboo on 2008-10-02
You should be able to do the same when converting to Ubunntu as you did when you converted from Mandriva to Opensuse.

JIm

---

### Post by caljohnsmith on 2008-10-02
> **Kirk Abbott said:**
> Currently I have a dual-booting system using Opensuse and XP. I want to replace Opensuse with Ubuntu because Ubuntu is better able to use the touchpad as a mouse than Opensuse is. 

However, when I try installing, the only options that I get are:

  1)Take over the entire drive
  2)Split the existing Windows partition, while leaving Opensuse in place.
  3)Do it manually.

I want to keep XP, and I don't want to keep Opensuse. So I figure I need to do it manually. I did check with documentation, but want to make sure I understand things correctly.

If I just delete the existing Opensuse partitions prior to going through the partitioning part of the installation, would the installer know to use that in place of dividing the windows partition, or is there something else that I need to be doing as well?

I originally moved from Mandriva to Opensuse because the Opensuse installer knew to just replace Mandriva while leaving the Windows partition alone. Basically I just want to repeat that, but move on to Ubuntu.

Kirk
You could delete or format the OpenSUSE partition prior to using the Ubuntu installer by using the gparted partition editor; press ALT + F2 and then run:
```
gksudo gparted
```
But it shouldn't be necessary. Just use the "manual" install option and choose the OpenSUSE partition as the place to put the main Ubuntu install (mount point "/"), and if you have a swap partition you can tell Ubuntu to use that too. That's about the most I can help from my memory of doing the install myself, but if you have more specific questions, feel free to ask.

---

### Post by kruisa7 on 2008-10-02
To install Ubuntu, you need at least one partition for root and one for swap.  Even better if you have one partition also for /home.  Then when you change from one distro to another, /home remains undisturbed.

If your disk has an ext3 or similar partition and a swap partition plus the vfat OR NTFS for Windows, just use the existing ext3 partition, (which can be resized giving you free space to create a new partition, if you want one for /home or anything else).  Your opensuse will then be replaced with Ubuntu and the windows partition(s) will be unaffected.

Once you have the partitions set up, then choose mount points, (except for swap).  Once Ubuntu runs, windows will be accessible according to your mount point.

Hope this helps you.:)

---

### Post by Kirk Abbott on 2008-10-11
Hello,

I lucked out last weekend in that I was able to attend a group meeting where someone was able to resolve the issue for me. I was also upgraded to what I think is 8.041. Still, thanks for the responses.

Kirk

---

