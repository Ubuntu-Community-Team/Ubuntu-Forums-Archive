---
title: "Waiting for info to continue install of Studio..."
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by Bobsteroid on 2011-05-24
I've posted elsewhere about partitioning but I ended up figuring it out. BUT I have another question...
 
Here is the situation: I have a 2TB external hard drive hooked via eSATA. The computer it is hooked to is running Win7 64 on a 500GB internal drive. I have used Gparted to put a 1.5TB NTFS partition at the end of the drive to use as a backup for another external drive and possibly an image of Win7 (a "back-up"). The NTFS partition is recognized and accessable by Win.
 
The rest of the "front" part of the external drive (about 400GB) I have begun to install Studio (64-bit) and let it do its thing. This is my second install attempt.
 
The first time, I didn't pick anywhere for GRUB to install so it didn't (ie: I left the "destination device" spot empty because I didn't like any of the other choices. I figured it would give me more options, but it didn't. I DO NOT WANT TO INSTALL GRUB ON THE INTERNAL DRIVE--AT ALL! Win7 is working fine and I need it to stay that way. When I rebooted and selected the external drive in BIOS to boot to, I ended up with a blinking, non-responsive cursor. Changed back to the internal drive to boot to and Win boots fine.
 
Not finding what I needed to know reading many pages of forums, I just reinstalled Studio as it seemed to be the least time consuming. Now I am at the "install the GRUB loader on a hard disk" page. Install wants to load GRUB on the MBR of the internal hard drive and I don't want it to as mentioned above.
 
The next page asks for a bootable device (/dev/" ").
 
QUESTION 1: What do I enter in the quotes to get Studio to boot from a USB thumb drive? I will be selecting "USB" as number 2 in the BIOS with CD as number 1 and internal HD as number 3. This way, when I want to run Ubuntu, I just stick the thumb drive in.
 
QUESTION 2: Where do I get a "live" CD or files for a USB compatible with Ubuntu Studio 64-bit? There are many references to a "Live USB" bootloader but I can't seem to find out where to download the files to load to the thumb drive.
 
Thanks for your help! Bob
 
UPDATE Q1: ended up figuring what device to load GRUB on which is "sdb". To load Ubuntu, I have to go into BIOS and change the boot hard drive to the external drive--NBD... Currently downloading updates: 90MB worth! :eek: Reminds me of Windows... :rolleyes:
 
The beauty of having 2 different drives with 2 different MBRs is that if one goes bad, I still have the other. They are independent of each other. In fact, I could disconnect the internal drive and just run Studio off of the external drive. But more likely will be that I will turn off the external drive and run Win. from the internal. Flick a switch and the external will fire-up (hot swappable) and I can access the NTFS back-up space on it.
 
UPDATE Q2: I figured out what a "live" CD is. And there apparently isn't a "live" version of Studio anything--I'd have to use the "regular" 64-bit version.
 
Also, to create a "live" USB stick, "netbook x86" is used and is only 32-bit.

---

