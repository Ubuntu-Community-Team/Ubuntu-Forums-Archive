---
title: "No option to dual boot after install."
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by Cwiddy on 2006-06-11
Well I havent used linux in about 4 years so I thought I would give it a shot again. 

Booted the live cd and double clicked on the install icon, selected a drive, everything seemed to go fine,  gave me a dialog to reboot, so i decided to reboot, removed the CD, computer reboots

Couple seconds later I see the Windows xp boot screen. 

I think this might have to do with my drive set up. 

/dev/sda (160 gig) <-- windows D: drive 
/dev/sdb (74 gig) <-- windows C: drive and teh drive that has \windows and this is the drive that boots
/dev/sbc (250 gig) <-- windows E:

installed it on my 250 so it is 200gig ntfs followed by an ext3 partition followed by the logical swap drive

I am guess grub went to the wrong drive.

Any help would be greatly appriciated.

-C

---

### Post by glacialfury on 2006-06-11
This isn't a permanent fix, but I just did about the same thing. You can still access the linux; when your computer starts booting, go to the boot menu - for me, that means hitting F12.  It should ask you what boot device you want to use.

Select hard drive; after that, you should have an option to select *which* hard drive.  I select the hard drive that contains the partition I installed ubuntu on, and it will then load GRUB, which will allow you to choose Ubuntu or Windows.  Note you have to do this every time you boot the computer.

I just installed last night, so I don't have a better option for you yet.

---

