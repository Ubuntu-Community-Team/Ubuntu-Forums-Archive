---
title: "Need a little help!   (Newbie question)"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by JHMac on 2009-11-19
I have recently installed Ubuntu v9.10 on my Dell Inspiron laptop and love it.  I have decided to upgrade my harddrive to a larger one and don't want to have to completely reinstall Ubuntu from scratch  (got it set up the way I want now)   Is there any way to just copy all of my original setup to the new drive without going through the complete install and setup again?      A big thanks to the Ubuntu team for a great OS package and freeing me from the Microsoft over bloated crap they call an OS.


Thanks for your help!
JHMac

---

### Post by darkod on 2009-11-19
CloneZilla seems to be preferred tool for imaging, it can read ext4 (I think?) ext3 and ntfs and for these filesystems that it can read it just images the data, not whole partition (empty space).
Download the image, burn on CD, boot with it and image the drive (to a usb hdd I guess). Switch drives. Boot with clonezilla again, put image back. That's the theory, haven't tried it myself coz new to ubuntu and I was just reading about backup options yesterday.

---

