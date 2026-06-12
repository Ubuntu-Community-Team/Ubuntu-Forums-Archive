---
title: "Installing Windows XP After the Fact, On a Separate Drive"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by kidford on 2007-04-03
I have Ubuntu Edgy Eft installed on my desktop computer.  It works very, very well, but I currently need to install Wndows XP on this computer as well.  I've tried running VMWare and, while it works, it is very slow - and doesn't work perfectly.  So I'd like to dual boot.
The problem apparently lies in the way that I want to install Windows XP.  My Ubuntu installation is on my IDE drive, with my home directory mounted from a separate SATA drive.  This SATA drive is the drive I'd like to install Windows XP on.

However, when I pop in the Windows XP installation CD and get to the partition selection, I'm confronted with a problem: Windows thinks it just HAS to write something to the MBR, which is on the IDE drive, where Ubuntu is, and consequently cannot be read by Windows.
The error screen I get is:

> To install Windows on the partition you selected setup must write some startup files to the following disk:
xxxxx MB Disk 0 at Id 0 on bus 0 on atapi [MBR]

However, this disk does not contain a Windows XP compatible partition.
To continue installing Windows XP, return to the partition selection screen, and create a Windows XP-compatible partition on the disk above.  If there is no free space on the disk, delete an existing partition and then create a new one.
To return to the partition selection screen, press ENTER.

Crap like this is why I've stopped using Windows for my primary computer - Windows just KNOWS it absolutely HAS to do this, and offers no way around it.
I'd like to be able to install Windows WITHOUT reinstalling Ubuntu as well, which I see the likely consequence of messing around with the partitions on my IDE drive.

My SATA drive has two partitions, the first of which is the partition I've set aside for Windows.
(For what it's worth, my IDE drive is "hda" and my SATA drive is "sda")

I've tried searching Ubuntu Forums for relevant topics, but haven't found the magic bullet yet.

Does anyone have an easy solution to this?
Thank you very much.

---

### Post by confused57 on 2007-04-03
You could try setting your SATA drive as the first hard drive booted in bios before installing Windows...or just disconnect your IDE drive.

Once you install Windows, hopefully, reset your bios boot order to boot your IDE drive before the SATA drive, then add an entry to grub to boot Windows...something like the one in the 3rd link in my signature.

You might want to check out the output of:
```
sudo fdisk -l
```
the -l is a small "L"
before installing Windows...your partitioning numbering could change, which would affect your /home partition as it is now mounted...unless you already have a partition formatted on sda1 & you're just overwriting it with Windows.

These are some things you might consider for getting Windows installed.
It shouldn't hurt anything for Window's to install it's IPL code to the mbr of sda.

---

### Post by kidford on 2007-04-03
Thanks Confused, that worked perfectly...
It wasn't immediately apparent to me that changing the hard drive boot priority would have the desired effect - I wasn't even trying to boot from the hard drive, after all.
I guess I shoulda tried looking at the forums a little longer, maybe when I didn't have a migraine already :)

---

