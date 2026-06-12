---
title: "IS it possible to create a &quot;system restore&quot; on a USB drive?"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Stray Wolf on 2010-04-04
I'm using an Ubuntu Karmic for AMD64.  I know I'd have to unmount my drives.  My root, swap, boot are on one internal HD and "home" is on the other.  So, I'd have to run a LiveCD, or create a bootable partition on my 320Gb usb drive, which is where I'd like to put my system restore.  By system restore I mean a bootable copy of my system, it's configuration, software and their configurations, and all my personal files (without compressing the thousands of photo's I have).  It'd be great if it worked like a LiveCd (only off USB)  Is this possible?

---

### Post by gare on 2010-04-04
hi -

Making a bootable USB is now as easy as:

1. download an iso of your desired system from place like:
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

2. System > Administration > Startup Disk Creator ( is name in 10.04,..something similar in 9.10 ..)
 It will make your usb drive a startup disk.  Guess you could copy your files onto any remaining space.. (your entire /home folder)...

---

### Post by solitaire on 2010-04-04
I'd recomend Remastersys
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
i've used it to create a "LiveCD" version of my install as well as backup disk...

---

### Post by Stray Wolf on 2010-04-04
OK!  Thanks.  So, there's a couple of options to compare.  I've used UCK with the USB Start-up Creator to modify a downloaded ISO of Ubuntu, but the outcome isn't quit the same as creating an image of my current system build. Besides, you can't copy a drive while it's in use can you?  Wouldn't I have to unmount the drives to make an image of them?  If I can make an ISO of my system I could use the USB disk creator to make a bootable disk.  I've already used GParted to create ample  bootable space in a partition.  More than enough to save my current build.  And I also left enough space partitioned in ext.4 for my home folder.  I'll check out that Remastersys and see what I can do with that.

---

### Post by psusi on 2010-04-04
One option is the partedmagic cd/usb.  You can set up a partedmagic cd or usb stick to have a mimimal boot environment useful for backup and recovery.  You can boot that and use the included Ghost4Linux (G4L) program to dump your entire root filesystem to an image file on a back disk, and restore it later if everything goes all pear shaped.

---

### Post by Stray Wolf on 2010-04-05
I'm not sure what's meant by a minimal boot recovery.  To dump my root in would take super user status right?  I tried "sudo file-roller" to archive my root (excluding /pictures,/music,/videos) but got an error...not a permissions error.  I'll add parted magic to the list of possibilities.  I'm starting to wonder if I can't just use Brasero from the LiveCD as a super user and just do an image of my HD's to my USB that way...then use UCK (Ubuntu Customization Kit) on the ISO to make sure it's bootable...lot's of tinkering ahead either way.  With what you guys use, are you able to just reinstall your system with all personalized software and configs if not media?

---

### Post by libssd on 2010-06-13
> **solitaire said:**
> I'd recomend Remastersys
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
i've used it to create a "LiveCD" version of my install as well as backup disk...
I had no problem creating both USB and DVD bootable backups with Remastersys and Ubuntu 9.04 with legacy grub. However, with 10.04 and grub2, I have been completely unable to create a usable USB backup. DVD works fine. Not sure what I'm doing wrong, but it would be nice to be able to restore from a USB, since I have a netbook with no built-in optical drive.

---

### Post by Stray Wolf on 2010-10-18
I found a solution that fits my needs perfectly.  CLONEZILLA ([http://clonezilla.org/)!]("http://clonezilla.org/")

---

### Post by simar.mohar on 2010-10-18
You can use use partimage. By ...
```
sudo apt-get install partimage
```
and then
```
sudo partimage
```

This will save the complete drive as a restore point..

---

