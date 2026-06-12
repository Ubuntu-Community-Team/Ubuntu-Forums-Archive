---
title: "USB booting issues"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by jgclark123 on 2007-06-21
I've got a bit of an odd problem, and I hope someone can help.  

I have Windows XP (rarely used) on one hard drive, Windows Vista (main OS) on another, and a third with no OS.  I wanted to install Kubuntu 7.04, but without screwing up my bootloaders, so I installed with /home mounted on the first hard drive (C: in both Windowses) and / mounted on the second (D:) (swap is on the third drive [E:]).  

To prevent bootloader screw ups, I installed /boot on a USB thumbdrive, hoping that when I boot without it plugged in, I'll be greeted by Windows Vista's bootloader, but when it is plugged in, I'll get GRUB.  Thankfully, that worked surprisingly well.  I can even still get to Vista (haven't tried XP, and I don't really care).  

However, I can't seem to boot Ubuntu, Ubuntu (recovery mode), or memtest from GRUB (those are the only three options).  All three led to a blank screen with just a text cursor blinking (on both monitors).  I tried using 'e' and changing the hd(0,0) to other stuff, and I only got "Partition doesn't exist", "Device doesn't exist", or "Filesystem not mountable".  (Yeah, I paraphrased.)  I'm not sure what the issue is, and I can't get into Ubuntu to run "fdisk -l" or anything like that.  I have no idea what HDD is being mapped to what number (as in hd(0,0)) or letter (as in sda1).  

If it helps, my motherboard's boot priority is USB, then CD/DVD, then HDDs (C:, then D:, then E:), but because the third drive (E:) is plugged into a PCI SATA card instead of the motherboard's SATA ports (it only has two), the Ubuntu alternate installer put that drive first.  (It was E:, C:, D:, USB drive.)  Each non-NTFS partition is after the NTFS.  (So on C:, it's 8 MB of unallocated [stupid Windows installer], 285 GB of NTFS, 15 GB of Ext3.)  

Thanks in advance, I've really getting confused here.


Edit: Wow, I feel really dumb.  It turns out it was taking minutes just to load /boot off the USB drive.  (I noticed GRUB was taking a little longer than usual.)  I still can't get KDE to start up, so I guess I'll just reinstall normally.

---

