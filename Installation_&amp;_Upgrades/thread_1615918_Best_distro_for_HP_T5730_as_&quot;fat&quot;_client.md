---
title: "Best distro for HP T5730 as &quot;fat&quot; client"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by underquark on 2010-11-07
From anyone who has modded a similar thin client to use it as a standalone PC, thoughts, please on which version of xubuntu likely to give best results for web browsing (including Flash), using OOO and basic photo manipulation but no video editing or other high-end stuff on the following machine.  I've seen that the video drivers can give problems with the installed graphics card ([http://ubuntuforums.org/showthread.php?t=1221221&highlight=T5730](http://ubuntuforums.org/showthread.php?t=1221221&highlight=T5730)).  Am I best going for Meerkat or finding an older version such as 8.10?

Hewlett Packard "Thin client" T5730 with:
AMD Sempron 2100+
RAM 1GB
ATI Radeon X1250

I plan to remove the Flash memory with embeded Windows XP and install a 160GB PATA drive.  I've got the cable and the case has been modded to accommodate everything. I'd be installing xubuntu from a USB stick if possible or borrowing a USB CD drive.

---

### Post by underquark on 2010-11-25
To answer my own question, there is no "best" distro.

I had a look for xubuntu 8.10 but many sites had dead links.  So I fitted a hard drive (160Gb 2.5" IDE, Samsung Spinpoint HM160HC), downloaded xubuntu 10.10, used USB Startup Disk Creator to put it on a 1Gb USB stick and then encountered an error on trying to install.  Found a post on this forum detailing the error* and the need to edit one of the config files, tried again and all was well.  Downloaded Open Office.  Minor graphic glitches on exit but fine in normal use.

The result is a whisper-quiet little PC that can be used for web browsing and general document work, connecting to my PVR to download films, connecting to my remote controls for programming them (it has serial and parallel ports for connecting to home-made JP1 cables) and, I suspect, I can hook it up to my TV with a VGA or DVI-to-HMDI cable and either stream video or play back using VLC.

Currectly connecting to network via a HomePlug but I see that there is space inside the box that would accommodate a USB wireless dongle, temperature permitting.

*On the USB stick open the file /syslinux/syslinux.cfg
Edit the line "ui gfxboot bootlogo" to read "gfxboot bootlogo"
Save file

Later I read that simply typing "help" and [Enter] does the trick but as I have already edited the syslinux.cfg file and successfully installed 10.10 I haven't tried that.

---

### Post by GeoGuinness on 2011-01-07
I'd certainly love to get 10.10 on a t5730 thin client, and I don't have a problem dropping a 16gb USB key in one of the inboard slots.  My concern is whether Ubuntu, or any other plain off-the-shelf linux distro is prepared to run without a hard drive at all, which is the case with a thin client.    And are there tools in Ubuntu to configure and deal with the enhanced write filter, or does that mechanism even exist under Ubuntu?  Essentially the flash looks like a hard drive, but flash has a limited number of write cycles, so we need some mechanism to ensure it is treated as a read-only device.    
 
GG

---

### Post by matttt on 2011-02-02
You can install debian 4.0 available at the HP website for the t5735 on your t5730 and HP offers a write filter add-on for linux as [SP46121]("http://bizsupport1.austin.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=12454&prodSeriesId=3634729&swItem=vc-78068-1&prodNameId=3634730&swEnvOID=4020&swLang=13&taskId=135&mode=4&idx=0").  Perhaps it could be made to work with ubuntu since it is debian based?  I don't know?  If you decide to revert back to windows there is a trick needed else you will get license error if you have any bios greater than 1.0 (bios bug).  Only difference between t5730 and t5735 is that Windows license is held in bios on t5730 and is not on t5735.

Windows Trick: Download both Linux & Windows XPe image from the HP site... extract both, to different sticks (or copy the flash.img (XPe image) & flash.dd (linux image) onto your local drive).  Be sure to use ONLY Win XPe 5.1.7 image, 5.1.8 will not work.

Make sure the last image you write, is the Linux one, replace "flash.dd" with "flash.img" and rename it to flash.dd

Insert the stick in your T5730 (or T5735, it actually doesn't matter) and do install, it runs 99% and stalls.  Remove usb and restart and windows completes 100%.  Then do shift key down log off to login as admin.

---

### Post by underquark on 2011-05-08
As an update, for those interested, the t5730 is running very well with xubuntu Maverick Meerkat.  Firefox and Open Office installed.

I've got my hands on another machine - it has a 1GB DOM (Disk On Module) so I might try to cram Puppy onto it and then use USB sticks as storage.  The price of 4GB sticks, in particular, seems to have dropped a lot recently and the bigger ones ought to get cheaper soon too.

A friend mentioned that lubuntu might be the way to go - anyone have experience of cramming it into a 1GB "disk"?

---

### Post by tajender on 2011-06-17
Could you please advise as to how did you go about installing a hard drive in your HP t5740w?
 
I am looking on to run LinuxICE on this one. Any help would be appreciated.

---

### Post by underquark on 2011-06-24
I have a t5730 and although I'm not familiar with the 5740 it might be similar.

There are two versions - the very thin machine and the double-thickness one where the additional layer contains serial, parallel ports and a PCI slot.  You need the thicker machine to physically fit in a hard drive - "with optional HP t5740/t5745        PCIe x4/PCI Expansion Module Kit".  [Link here]("http://h18000.www1.hp.com/products/quickspecs/13496_div/13496_div.HTML").

Disassemble the machine.  Note where the DOM (the SSD with the IDE interface) plugs into the mainboard.  Cut a slot in the "roof" above it wide enough to pass a small IDE cable through.  Make a suitable holder for the drive (I used a block of dense foam and cut it into a fairly open cradle so that it supports the drive, allows ventilation and doesn't vibrate against the chassis).  Remove the DOM and look for markings on the DOM or on the board to indicate which is pin1.  Plug in a 44-pin IDE cable which carries data and power to the drive.  Pass the cable through the slot, plug in the drive an away you go.  Worth installing as much RAM as the machine will accept.

Haven't tried LinuxICE but had Puppy, PeppermintOS and PeppermintICE working briefly.  These are all suited for a machine without a hard drive.

In another post I described getting what is effectively lubuntu working on a machine with 2GB SSD and with one 4GB USB stick housing /usr and /var and a second 4GB USB stick for it meagre storage requirements.

---

### Post by DarkZrobe on 2011-07-01
I also have the T5730 as a home server media machine. I have had it up and running for almost two years running Linux Mint 8, 9, 10. I purchased the addon module that attaches to the side so I could add a sata card and a external esata hard drive. It has worked beautifully since then. Using a USB thumb drive worked nice for a few months but a little slow. This sata card rig works sooo much better. I would love to see if anyone else has made any other modifications to theres. Kinda looking to hook a magic jack or something similar to it since it is on all the time.

I think the only problem I have had with it is the graphics card. The drivers for it dont appear to exist... Would love to utilize that a little more but at this point I am quite happy with how everything turned out.

---

### Post by DarkZrobe on 2011-07-01
O and I have played with all of these versions of thin clients. The T5740 is a little faster but puts off more heat (They have the N280 Atoms) I need to check if the graphics card works better on those. There is also some high ends like gt7700s or something that have a dual core AMD Turion in them that are also much faster but they have a fan in them and are really pushing the limits of being a thin client.

---

