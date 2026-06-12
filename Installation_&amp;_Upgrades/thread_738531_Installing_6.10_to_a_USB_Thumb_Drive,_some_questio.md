---
title: "Installing 6.10 to a USB Thumb Drive, some questions"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by greatgoo on 2008-03-28
I read the various posts about Ubuntu on a thumb drive.  I went to Pendrivelinux.com and read what was there.  Then I did my own thing, no one said I couldn't.

I bought a PNY 4 gig thumb drive and wondered if I could install onto it from the CD.  I found the main issue was with the partitioning of the drive.  If I umount before each step then the partitioning would work.  Failure to do that caused the partitioner to fail.  To prevent the partitioner from seeing the hard drive I unplugged it.

SO!  I partitioned the thumb drive with a 3gig ext3 set to boot, a 400meg set to ext3 and a swap using the rest of the drive.  The cd loaded to the thumb drive just like it did to the hard drive, though slower.  When I tried to boot from the thumb drive I got a grub error 18.

I looked at the thumb drive with windows, it sees an empty drive.  I looked at it with my Ubuntu machine and it sees the linux partitions.  Kinda cool, but slow.  So, grub error 18.  I know the disk is not beyond the BIOS limits.  Any other ideas?  I was thinking of maybe doing the live CD to a usb thumb drive.  Ubuntu on a stick!

David Davis
Toledo, OR 97391

---

