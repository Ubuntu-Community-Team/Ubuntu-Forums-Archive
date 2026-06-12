---
title: "DualBooting Xp and Ubuntu"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by Omega82 on 2007-03-07
Hello

I have been looking through the forum, but cannot quiet find what I'm looking for.  I have XP installed on one of my hard drives, I just installed Ubuntu onto another hard drive.  The installation finished and the system reboot, however it reboot right into windows.  I am not sure how to access Ubuntu or how to get windows to give me the opinion of booting either XP or Ubuntu.

---

### Post by rsambuca on 2007-03-07
The easiest way to dual-boot is to have the Grub loaded onto the MBR.  When you boot up, grub when then give you a choice of operating systems.  Normally grub is installed automatically when you install ubuntu, but sometimes it doesn't get the drive order right if you have more than one drive.  How many drives do you have, and what is their boot order in your bios?

---

### Post by bulldog on 2007-03-07
It matters on which hdd you installed GRUB.
If I read this you installed GRUB on the other hdd,so if you can,boot from the other hdd and see if GRUB comes up.

If you have trouble booting windows from your GRUB,don't worry,that's an easy fix.

---

### Post by Omega82 on 2007-03-07
My HDD are as follows
C: Windows XP
F: just  a storage drive, fromated by XP
G: the one I installed Ubuntu on

The boot order of the drives in the BIOS is a little confusing as 2 of the drives are Identical(F&G), size and manufacturer.   I can say that the C: drive is the first one, and then it would probably be the F and then G, as that was the order that I installed them into the machine.

---

### Post by bulldog on 2007-03-07
If you boot from the live cd can you type in a terminal the next command and copy the output to the forum?
```
sudo fdisk -l
``` it's an l as in like not a one.

---

### Post by Omega82 on 2007-03-07
I'm currently not at the computer I installed Ubuntu on, however if I was to change the order of the drives in the bios so that the G: drive (one I install ubuntu on) was first in the list the system should boot from that drive.  And if this GRUB program is installed with Ubuntu then I should be prompted with the option of which OS to boot up.  That is if I am understanding this correctly.  I will post that sudo fdisk -1 when I get back to my PC.

---

### Post by mikewhatever on 2007-03-07
> **Omega82 said:**
> I'm currently not at the computer I installed Ubuntu on, however if I was to change the order of the drives in the bios so that the G: drive (one I install ubuntu on) was first in the list the system should boot from that drive.  And if this GRUB program is installed with Ubuntu then I should be prompted with the option of which OS to boot up.  That is if I am understanding this correctly.  I will post that sudo fdisk -1 when I get back to my PC.

The command to type is > sudo fdisk -l and not **fdisk -1.**

If in doubt, that's an l for Larry.

---

### Post by Omega82 on 2007-03-07
Ok here is the sudo fdisk -l output from the terminal window:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37777   303443721   83  Linux
/dev/sda2           37778       38913     9124920    5  Extended
/dev/sda5           37778       38913     9124888+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

---

### Post by mikewhatever on 2007-03-08
> **Omega82 said:**
> My HDD are as follows
C: Windows XP
F: just  a storage drive, fromated by XP
G: the one I installed Ubuntu on

The boot order of the drives in the BIOS is a little confusing as 2 of the drives are Identical(F&G), size and manufacturer.   I can say that the C: drive is the first one, and then it would probably be the F and then G, as that was the order that I installed them into the machine.
In order to boot into Ubuntu, you have to change the boot order in the BIOS. Either F or G should be the first one. Try both, since you do not know which one has Ubuntu on it. If GRUB is installed to Ubuntu HDD MBR, it should load and boot Ubuntu.

---

