---
title: "Problem installing Ubuntu on new Hard-Drive via USB"
date: 2013-04-22
forum: Installation &amp; Upgrades
---

### Post by BeKindToTheNewKid on 2013-04-22
Hi All, 

First post on here, so apologies if I'm bringing up a problem already solved - if so, please do point me in the right direction. 

My old hard-drive seems to have stopped working - it's given me the blue screen of death. I had partitioned it previously and was running Windows 7 and Ubuntu. I've since installed a new 1TB Western Digital hard-drive, which BIOS seems to recognize. However, when I try to install Ubuntu via USB, it does not seem to find a hard-drive! It 'works' so to speak up until that point, in as much as Ubuntu loads, and I can run it off the USB drive, but when I try to install it, it says I am connected to the internet, which is one requirement for installation, but the other - having 4GB of space - has a big red cross next to it!

Any ideas? Many, many thanks in advance.

---

### Post by dino99 on 2013-04-22
the first things to check are:
- that hdd specs (doc)
- how the bios settings recognize that device : probably need the latest bios upgrade (if available); "ahci" setting might be the better choice 
- how gparted (the partition formatting tool) recognize that hdd : format it as "ext4"

example of standard installation: [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

note: to format a hdd, it needs to be unmounted; so boot with an other device, like an usb stick

---

### Post by fantab on 2013-04-22
> **BeKindToTheNewKid said:**
> My old hard-drive seems to have stopped working - it's given me the blue screen of death. I had partitioned it previously and was running Windows 7 and Ubuntu. I've since installed a new 1TB Western Digital hard-drive, which BIOS seems to recognize. However, when I try to install Ubuntu via USB, it does not seem to find a hard-drive! It 'works' so to speak up until that point, in as much as Ubuntu loads, and I can run it off the USB drive, but when I try to install it, it says I am connected to the internet, which is one requirement for installation, but the other - having 4GB of space - has a big red cross next to it!

I hope you have ascertained thoroughly that your OLD drive was indeed failing. Because for BSOD that is not the only reason. 

Does your New 1TB WD drive have a partition table on it?
When you boot from USB are you booting with 'PMAP' or 'UEFI'?

---

### Post by BeKindToTheNewKid on 2013-04-22
Whilst I am very very grateful for the first two replies, I don't really understand them! I love to tinker with computers, but I'm still an amateur in reality. 

In reply to post #2:

- I don't know how to check that the hdd specs?
- Interestingly, BIOS only recognised the drive when I put it in SATA 'mode' (might this be a clue?)
- Again, not clear on the third point

In reply to post #3:

- The old drive was certainly failing, although my father is double checking that for me with an external drive reader. It would sometimes load (often not) and would crash with blue screen as soon as I tried anything that might help it stop crashing in future. Registry clean, system restore etc all caused it to crash very quickly. 
- I'm not sure if it has a partition table on it. 
- I'm not sure about PMAP or UEFI - when I load my computer, I hit F8 and it gives me the option as to which drive to boot from. I choose USB. 

Hope that is vaguely helpful. Sorry for being an idiot.

---

### Post by BeKindToTheNewKid on 2013-04-22
Post #3 PS - The rest of the computer seems to work fine when running Ubuntu from a USB (sound, graphics etc), and it doesn't crash, which I guess is a good indicator that the old hard-drive was causing the problems?

---

### Post by fantab on 2013-04-22
To check your 'old' HDD you can use the utility, 'DISKS'. You can boot Ubuntu from USB, choose to "TRY UBUNTU"; once you have a desktop open 'DISKS' and run SMART Tests on it. That should tell you about the 'Health' of your old HDD. Also use it on your new HDD... just to make sure that are no manufacturing defects.

Are you still planning to Dual-Boot, Windows and Ubuntu? If yes, then have you installed Windows7? It will be wiser to install Win7 first, if you plan on Dual Boot. 
What are the spec of your Computer? That is, MotherBoard, RAM, Graphics, CPU...
What version of Ubuntu are you trying to install? 

As suggested in post #2, have you enabled "AHCI" mode for your SATA? Usually, there will be Three modes: IDE, RAID, and AHCI. If you have, by any chance RAID enabled then you have the kind of issues you are having. Confirm what mode is SATA set to.

Can you post a screenshot of your partitions from 'Gparted', the disk partition utility available on your Ubuntu USB?

---

### Post by grahammechanical on 2013-04-22
May I make a suggestion? Dino99 says:

> [COLOR=#000000]how gparted (the partition formatting tool) recognize that hdd : format it as "ext4"[/COLOR]

and Fantab says:

> [COLOR=#000000]Does your New 1TB WD drive have a partition table on it?[/COLOR]

What they mean is, if the new drive is not formatted then it is not recognised as a location to install onto. I recently installed a new 500GB internal drive. And I only cut my knuckles once!. To install on it I had to run Ubuntu in a live session and open Gparted. It is in the Dash. From there I could select the new drive. It might be seen as sdb (sda being the old drive). Once selected I could choose to create a new partition table and have the new drive formatted as Ext4.

Then I closed Gparted and while still in the live session I ran the installer. By the way, the installer might still see your old hard disk (sda). You will need to scroll down the little panel that asks us where we want to install Grub to. Don't let it install Grub to the MBR of sda unless you have disconnected the old drive.

Another thing to watch out for. The installer is smart enough to recognise the swap partition on the old drive and use that. This means that if you remove that drive the Ubuntu on the new drive will not find its swap partition. It is best to disconnect the old drive when you are installing. That will give you a swap partition on the new drive.

Do not worry about Ubuntu being confused as to which drive is sda or sdb. They are just labels. Each partition is given a UUID Universally Unique Identifier. So, when you re-connect the old drive it will switch to being sda once again with the new drive being sdb. I am speaking from recent experience.

Regards.

---

### Post by BeKindToTheNewKid on 2013-04-22
The plot now thickens. I tried to install it again when I came home, and lo and behold, this time, the installation process works, and ubuntu recognises my HD.....until it was nearly installed. And then it stopped! It said there was an error with either the DVD drive or the HD. Frustrating. But it recognsied it which is progress. 

Sadly, now it does not, and nor does BIOS. On any setting. Very annoyed now!! One step forward, two backwards. 

I can't respond to all of the technical questions now as I have to run and cook dinner and they will take me a while, I will try tomorrow morning. Sorry!

---

### Post by BeKindToTheNewKid on 2013-04-22
And just to be clearer; the old hd is no longer in my computer - so Ubuntu obviously doesn't see that either :-) As promised, will give further detail tomorrow.

---

