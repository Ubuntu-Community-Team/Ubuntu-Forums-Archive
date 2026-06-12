---
title: "Live CD - how to mount hds?"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by dogugotw on 2006-09-29
I've been running another Linux distro for a while.  Yesterday when I powered on, the boot failed - lots of problems with the file system.  I've been thinking about making the switch to Unbuntu so great time to make the jump.
BUT
I'd like to salvage a couple of files off my HD.  I believe I have some recent backups on a usb drive, but just in case I'd like to try and get the most recent version off the hd.

I've heard about using the live cds to rescue broken hds.  Stuffed it in, powered on, cannot figure out how to find and mount all of my hds and my usb drive so I can try copying stuff around.

I've searched the forum but not found anything that fits.

I come from a KDE environment so maybe I'm must missing something very basic.

Any assistance is greatly appreciated.

Doug

---

### Post by thephantomlinguist on 2006-09-29
When you plug in your USB drive, Ubuntu will likely find it (meaning an icon will appear on your desktop). If it doesn't, let me know and I'll see if I can walk you through mounting it manually.

As for the drives on your system, well, you'll need to know a little something about your system.

Here's the easiest way to do it:

Open a terminal and type the following:

```
sudo mkdir /mnt/temp
sudo mount /dev/sda1 /mnt/temp
cd /mnt/temp
```

Replace sda1 with hda1 or whatever partition number you need.

You should now be able to browse around and copy off anything you want to keep.

When you're done, just do the following:

```
sudo umount /mnt/temp
```

You can then mount another partition or do whatever else you need.

Hope this helps!

---

### Post by dogugotw on 2006-10-08
Many thanks for the information (and sorry for the delay responding).  
I wound up using Knoppix.  For this type of operation, Knoppix just seems to work.  Everything mounted and was visible.  I was able to copy my key directories and files to a network store without any problem at all.

I'm beginning to think I may have a full /var or /tmp directory.  After I got into this problem, I remember running into something similar before and it related to /var being full.

In the mean time, I've purchased a new 300 gig hd and am in the process of trying to fix a GRUB Error 18.  The good news is that the files I needed are backed up so no matter what happens, I should be ok.  I'm also able to re-think my whole system setup and build it so it makes more sense.  That, and there's nothing critical about the box since I have other systems I can use in the mean time.  

Thanks again for the assist.

Doug

---

