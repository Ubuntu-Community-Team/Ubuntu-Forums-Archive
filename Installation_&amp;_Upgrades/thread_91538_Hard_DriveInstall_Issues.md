---
title: "Hard Drive/Install Issues"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by theparadox1083 on 2005-11-17
My name is Patrick - this is my first post here.  I've been battling with my system for more than two days and I have still had no success.  I've searched many forums and found solutions, but each solution has created or lead to another problem and right now I've hit a wall.  I can't find any solutions to my latest problem.  I'll go through my situation and the steps I've taken so far.

I don't know if this belongs in the hardware forum or here in this forum, but it's a combination of both it seems - or at least I don't know which is causing the problem.
I am at work and pulling this all from memory.  I'll double check the details from home and make corrections if anything isn't accurate.

The initial problem:
I was running Kubuntu 5.04 on my system.  
System: AOpen AK77-333 with original BIOS, XP 2000+, 1GB+ of DDR (266 I believe, not that it should affect any of this), two 80GB Deskstars (different models, about 77 GB and 79 GB actual capacity), one relatively new CD/RW, one older 52x CD-ROM.

I was concerned that my old hard drives may be filling up soon, and I happened to see a 160GB Seagate HD for sale at Best Buy with some massive rebates dropping the price to $50 or so.  I installed the Hard Drive in place of the 52x CD-ROM.  I went to partition the drive with fdisk and everything seemed to work...but it didn't.  I checked the partition table with fdisk and alas, it wasn't there.  Nothing had been writen, even though fdisk seemed to have finished with no errors.  I tried parted as well as cfdisk and each seemed to work but never actually wrote the table to disk even though it indicated it had.  I pulled out a 5.10 live (KDE) disk and tried from there and got the same results with fdisk and cfdisk.  Now that I think about it, I believe fdisk gave a warning about 0x0000 and that (w)rite would fix it.  That warning never went away though, even after supposedly writing the table to disk.
So, as I was considering upgrading to Breezy anyway, I decided to wipe 5.04 and install 5.10 and try my luck with that - I'd seen partitioning problems in other forums and they mentioned that GRUB might have had something to do with it.  I know very little about GRUB but I know that it won't be running in the background while I'm installing from CD.  I ran into the same problem!  The partition software would claim to have written the table to disk, but when I went back to look at the partitions the new disk was blank. This is my first experience with a large capacity (>137GB) disk, so I thought perhaps this is what happens when my hardware can't handle it?  I could see it, and it registered in the BIOS correctly, but I couldn't touch the partition table.  So I tried it in my gaming machine (Motherboard is much newer) and had no problem partitioning from a Kubuntu 5.10 live CD.  So this seemed to indicate that the disk itself was fine.
I popped it back into the other machine and sure enough, the partition table was still there from the other machine.  I used the newly created partition and installed Kubuntu 5.10 without a single problem.  I left the install running in it's final stages, came back home and there was Kubuntu's login window.  I logged in, checked a few things out (it had successfully created folders in my home directory, which was located on the new 160GB drive), and to make sure things were in order I rebooted.  "Operating System not found" was the message I was greeted with after reboot.  This persisted after a few more reboots.  I installed it again - but this time the installer hung while formatting the new drive.  Interestingly, I noted that this time it formatted the drive completely, then formatted it again reaching 33% instantly the during the second format and then hanging there. Repeated the install, same outcome.
Fine, just in case this happened (though I don't know why it booted initially if there was a hardware problem) I had gotten an Adaptec Ultra ATA IDE Controller Card (I believe that's what they are called, I've never used one before) which specifically mentions that it supports high capacity disks.  I installed the card, connected the new 160 GB drive to it, and tried to install again.  I was able to partition the drive now.  The setup copied all modules, etc. to the disks (note that the only partition on my new HD has been /home), requested I remove the disk and then restarted.  Now I got some sort of GRUB Error, stage 1.5.  I tried again, this time placing my /boot partition on the new disk.  Same problem.  I went back to using the new disk only for /home and made sure that the /boot partition was flagged "bootable" (yeah, I should have checked that before) and now I'm getting "Operating System not found."  Extremely frustrated, I thought perhaps flashing the BIOS would enable me to partition the new disk using the motherboard provided IDE controller.  Installed Windows XP (interesting - I had to remove the new disk because windows was not able to boot from the other two while it was installed, and the new disk was not recognized because XP prior to SP1 does not support high capacity disks.  It showed up as 7.32 GB and I couldn't touch it with their install partitioning software) and ran AOpen's BIOS Upgrade utility and flashed the bios.  Now it has 1.19 (the latest, Oct 04).  I still cannot partition the drive while it's connected to my motherboard's controller.  Several posts I found also recommended I set the access type of my hard drives to "Large" to possibly fix my "Operating System not found" problem.  I can only do this to the drives connected through my onboard IDE Controller and can't see any way to change the settings of the drive on the new card.  Still, what I could do did not solved my problem.  Also, just a note, my other CD-ROM drive cannot be combined with the new hard drive using the onboard controller.  The new disk is read as gibberish followed by ) ) ) ) ) ) ) ) ) ) ) and the system hangs during POST.
NOW, the current problem:
When loading the installer with the new drive connected to the new ATA card, the installer hangs while loading the "Linux ATA" module, at 83%.  I tried disconnecting the drive and loading the installer and it loads without that problem.  I try to partition the drive using the new controller, and install using the old controller and it continues to freeze at the above mentioned point during a second formatting of the /home partition.  I'm totally dead in the water unless I scrap this new HD.  However, I sent in the rebates so I can't return it (and it seems to be working fine with other hardware so I doubt a replacement from the manufacturer would solve the problem) and I also can't return the ATA card...so I'd like to be able to use the $100 worth of equipment I've bought.  Am I doing something wrong here?  Any ideas as to why I am running into all these problems and how do I fix it?  I would really appreciate any help.  Also feel free to correct any of my terminology as I am mainly self-taught and would rather not look like an idiot the next time I ask a question in a forum.  ;)

Thanks again!

Patrick

---

### Post by yesplease on 2005-11-17
Can you check if your new bios supports large disks? (Edit: I think your motherboard supports large disk, check your manual for the BIOS settings)

If it does, you do not need the controller. (if you dont need the controller dont use it in this fase, but plug it in an iDE slot).

Can you check if the master/slave setup un the new hard disk is set up right? Check the cable, did you get a cable with this disk?)

Perhaps it is a good idea to make things a bit simpler in this stage: perhaps you can use the disk with XP as master and the large disk as master, and unplug the 3rd disk for now. Check if XP is still on the C-partition after you do this.

Can you give us a summary of how your disks and partitions are arranged now, for instance the info from gparted?

---

### Post by theparadox1083 on 2005-11-17
"Can you check if your new bios supports large disks? (Edit: I think your motherboard supports large disk, check your manual for the BIOS settings)"
-Yes : Max Disk : 144,000,000GB [by 48 bits LBA Spec.] 
[http://usa.aopen.com/products/mb/ak77-333.htm](http://usa.aopen.com/products/mb/ak77-333.htm)

"If it does, you do not need the controller. (if you dont need the controller dont use it in this fase, but plug it in an iDE slot)."
-After checking out my motherboard I agree.  However, if the drive is connected to my motherboard (and not through the controller) I cannot partition it, and now that I've updated my bios, I can't load the installer (hangs when loading module for "Linux ATA Disk").  If I connect the drive through the controller, I am able to partition and the installer does not hang.

"Can you check if the master/slave setup un the new hard disk is set up right? Check the cable, did you get a cable with this disk?)"
-I'm pretty sure it is set up correctly.  I am a relatively experienced computer technician (not a linux master though) and I don't bother loading the installer if the BIOS doesn't display all of my drives at startup.  I've tried:
Primary- M 160GB Seagate, S CD-RW (and I've switched them)
Secondary- M Deskstar, S Deskstar
also tried:
Primary- M CD-RW
Secondary- M 160GB Seagate
The only set up that doesn't cause the installer to hang is:
Primary- M CD-RW
Secondary- Deskstars
Controller Prim/Sec M/S 160GB Seagate
(edit: The cable is either the one that came with the disk or the shielded round cable that I was using on the other two deskstars.  I've tried both cables.)

"Perhaps it is a good idea to make things a bit simpler in this stage: perhaps you can use the disk with XP as master and the large disk as master, and unplug the 3rd disk for now. Check if XP is still on the C-partition after you do this."
-I don't actually have XP installed currently.  I only installed it to run the BIOS Update, then wiped the drive again.  I'm not looking to dual boot, I only want one OS. (edit: Also, as you can see above I've tried bringing it down to basics as well.  Just the CD-ROM and Large disk.  Still hangs when loading "Linux ATA Disk" module.)

"Can you give us a summary of how your disks and partitions are arranged now, for instance the info from gparted?"
-I've tried all sorts of different partition tactics, as I mentioned in my first post.  Since I can't actually get to unpacking the modules/finishing the install, I don't really have a current summary.  My original plan was to combine all leftover space using LVM/JBOD for my /home but I get errors when I try to create LV Groups...so just what I'm shooting for is:

79GB Deskstar:
  4GB /boot (bootable)
  4GB /swap
  71GB /
77GB Deskstar:
  77GB /usr
160GB Seagate
  160GB /home

Granted, it's a lot of wasted space but I'm not looking for efficiency at this point, I'm looking for anything that will install.  Again, please be aware that I've tried putting the boot partition on other disks, I've tried LVM...nothing has worked so far.

Patrick

---

### Post by theparadox1083 on 2005-11-17
I'm going to see if I can roll-back the BIOS so to speak.  Install an earlier revision.  Hopefully this will prevent the installer from hanging while it loads...even though I can't partition the drive while it's connected through the onboard controller.  The only that changed and could have caused it to hang while loading is logically the BIOS.

---

### Post by theparadox1083 on 2005-11-17
For whatever reason, I finally able to edit the partition table using the Windows XP installer.  That's great...but I can't load the Kubuntu installer without it crashing...I'll check back after I try to roll back the BIOS and beat my head against the wall some more.

---

### Post by poptones on 2005-11-17
As I read this I thought to myself "I wonder if this is a Via motherboard?" So I looked it up and... sure enough, my hunch was right. I've seen this same kind of craziness when trying to install mandrake on a system that had a via motherboard... a *bad* via motherboard.

Dude... you got a bad motherboard. I'll betcha.

---

### Post by theparadox1083 on 2005-11-17
Well, that would just be the icing on the cake.  I've had no problems up until now - and I have no problems loading XP, save for the fact that pre-SP1 doesn't support large capacity disks.  However, when Ubuntu or as I just tried Linspire load their installers while my new drive is connected to the onboard controller, they both hang.

---

### Post by poptones on 2005-11-17
Yeah, go over to the "linux humor" thread and read the little four line ditty about windows users, mac user and linux users... Windows can work with some amazingly bad hardware - at least until you have to reinstall. That's when the bad motherboards really rise to the surface. You have no idea how many people I've encountered with five year old machines (or even older) who, after getting totally hosed by spyware and virii decide to reformat and then discover they can't get windows 98 to reinstall.

Come on.. you wanted a new motherboard anyway, didn't you? You can get a shiny new motherboard with a cool running XP2600M cpu for a hundred bucks!

---

### Post by yesplease on 2005-11-17
The motherboard can be bad, but that is not yet the conclusion.

I already checked your mainboard on the Aopen site, and with the checking manual for BIOS settings, I meant the BIOS settings for large disks (if any). I asked for a summary because your post is rather long :) and almost nobody will try to figure out what your final setup is.

I read somewhere that the i368 kernel can only handle less than 2 GB swap.

One more question, are the partitions on your install disk ext3 (I mean no fat)?

If you want 1 OS, then I would suggest to try it first with only 1 of the old disks (which worked before), with only ext3 partitions (disk as master and CDplayer as master). 

I am not saying that this is going to work, just that it is better to remove the clutter, and that it is a good idea to check all settings on the hardware and bios again. Hope it helps, or that somebody has better advice for you,  good luck.

Oh, and I am not a linux guru at all.

---

### Post by theparadox1083 on 2005-11-17
Yeah.  I give up.  I'm installing everything on the old drives again.  So far no problems.  I'm convinced there was some sort of a hardware conflict concerning the new drive.  I'll deal with a small amount of space until I've saved up enough for a new motherboard and processor - my newer motherboard had no problems with it.  My server needs to get with the times anyway.

As far as the partitions went I used only ext3 (save for the swap).  I appreciate all of the help, though I'm kind of bummed that my investment went to hell.  Take care all!

---

### Post by yesplease on 2005-11-18
[QUOTE=theparadox1083]Yeah.  I give up.  I'm installing everything on the old drives again.  So far no problems.  I'm convinced there was some sort of a hardware conflict concerning the new drive.  I'll deal with a small amount of space until I've saved up enough for a new motherboard and processor - my newer motherboard had no problems with it.  My server needs to get with the times anyway.

As far as the partitions went I used only ext3 (save for the swap).  I appreciate all of the help, though I'm kind of bummed that my investment went to hell.  Take care all![/QUOTE]

This shows that your mainboard is not broken. Note that you did all the hard work already, new bios and even a reinstall. The plan was offcourse to run the OS on the old disk and later plugin the large disk as master (without controller) and use it for data. Then post error messages, if any.
The worst thing that can happen is that you have to reinstall Ubuntu, which isnt much work when you havent tweaked it yet.

You probably have done a global search for compatibility issues for the large disk (and its controller)?

---

