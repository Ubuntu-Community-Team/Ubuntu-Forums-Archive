---
title: "Reinstalling Vista To Dual Boot"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Lster on 2007-12-09
I recently got a new laptop (Acer Aspire 5920G) which has Vista on it. As I much prefer Ubuntu I installed it (deleting all other partitions). I still want to use Ubuntu but I want to install Vista first and then Ubuntu to dual boot with it.

So I went to reinstall Vista. However, when I put my Acer eRecovery disks in and boot from them, I get an error (and I am told I have to reboot). I have searched, but I wasn't able to find anything useful. It appears to be something to do with a hidden partition (that I must of deleted installing Ubuntu), that is used for recovery? Is this right? Also, topics on this seem to be talking about the MBR...

Am I anywhere near right? Any hints to reinstalling Vista, after which I am fine doing the rest, are greatly appreciated!

Thank you,
Lster

---

### Post by fmartinez on 2007-12-09
1. you are right about the recovery drive (it's not hidden... it's listed as recovery), it's usually standard on OEM's computers that ship with Winodows. It has information that will restore a computer back to the way the OEM sent it. 
2. Are you able to actually boot from the Recovery CD? 
3. Where does it take? 
4. At what point does it ask you reboot at? 
5. You maybe forced to send it back to the OEM to have it restored if you cant get it from the CD.

---

### Post by tommcd on 2007-12-09
First, a question: where did you get the recovery discs? Did you burn them from vista? The reason I ask is because about 6 months ago I bought an Acer Aspire 3680-2633 laptop with vista that came without recovery disks, but you could burn them from the recovery partition.
My laptop came with 3 partitions:
1) a working vista partition
2) a backup partition for Acer's backup utility
3) a recovery partition
I did not bother with any of it and I blew away vista to install several distros. Anyway, it may be necessary to keep that recovery partition to reinstall vista. 
How big is the recovery CD? Stick it in your cdrom drive in ubuntu and right-click on it  and choose properties. It should be pretty big if it is a full vista restore disc.

---

### Post by Joeb454 on 2007-12-09
It shouldn't even be a CD if it's a Vista Restore Disc, purely because Vista is about 3gb on disc lol

---

### Post by AgentZ86 on 2007-12-09
> **Lster said:**
> I recently got a new laptop (Acer Aspire 5920G) which has Vista on it. As I much prefer Ubuntu I installed it (deleting all other partitions). I still want to use Ubuntu but I want to install Vista first and then Ubuntu to dual boot with it.

So I went to reinstall Vista. However, when I put my Acer eRecovery disks in and boot from them, I get an error (and I am told I have to reboot). I have searched, but I wasn't able to find anything useful. It appears to be something to do with a hidden partition (that I must of deleted installing Ubuntu), that is used for recovery? Is this right? Also, topics on this seem to be talking about the MBR being invalid for Vista or something?

Am I anywhere near right? Any hints to reinstalling Vista, after which I am fine doing the rest, are greatly appreciated!

Thank you,
Lster

I pretty sure the deal with OEM distibutors is NOT to provide the OS on the DVD, most likely the Vista restore disk is a DVD restore disk and will not boot to the DVD itself or install Vista it's only a restore disk that uses your restore partition.

You will most likely have to contact the vendor in order to see about getting a replacement, I would guess they will send you another harddrive with the restore partition on it so that you can utilize your restore Vista DVD.

It's due to some deal with MS and the OEM builders required the OEM's NOT to provide the actual OS Re installation disks anymore. at least thats what I've read all on the net and from other OEM builders sites.

So in addition with Vista this creates partition problem since there is a 4 primary parition limit so if you have the OS on one partition and the restore info on another partition and with Dell you also get a utility partition. That makes 3 primary partitions so this means the Ubuntu and most linux distros will not be able to give you a Ubuntu partition and a swap partition without first deleting one of the partitions either Vista,restore,or utility. This creates a conflict for most OEM computers now days. It was easy with XP cause you typically have a re-installation CD, but now with Vista it's a problem.  Even if you try to resize, cause you can't just create an extended partition and logical partitions you have to remove at least one partition first I"m guessing the utility partition and then create logical and extended partitions, and resize your Vista, partition etc.

It's pain, but would be simpler if there was an actual reinstallation Vista DVD or CD

I hope this helps I would contact the vendor or perhaps get a Vista CD for re installation purposes.

OEMs should provide the restore partition in a logical / extended partition then you would simply be able to expand it and add additional extended partitions etc. as needed for your other Distros. 
This could very well be another monopoly violation with MS cause they can't force you to have only their OS on your computer by taking up all the primary partitions.

Anyhow hope this helps.

---

### Post by Lster on 2007-12-09
> **fmartinez]2. Are you able to actually boot from the Recovery CD? [/QUOTE]

Yes (it's a DVD).

[QUOTE=fmartinez]3. Where does it take? [/QUOTE]

I boot from the DVD and it asks me to pick a language (English). It then tells me to plug in the AC cord and a couple of other warnings, then it goes to the copying files screen and an error pops up. When I click "OK" it reboots...

[QUOTE=fmartinez]5. You maybe forced to send it back to the OEM to have it restored if you cant get it from the CD.[/QUOTE]

I'd rather keep Ubuntu. I miss Vista for games, but Linux equivalents are not too bad (Sauerbraten and AssaultCube are excellent!).

[QUOTE=Joeb454]It shouldn't even be a CD if it's a Vista Restore Disc, purely because Vista is about 3gb on disc lol[/QUOTE]

It is 2 DVDs said:**
> This could very well be another monopoly violation with MS cause they can't force you to have only their OS on your computer by taking up all the primary partitions.


Well, I'm one less user of Vista - it's there loss! If they keep on like this, they won't have a market share!

Ah well! I guess I made the full switch sooner than I intended! Thank you all for the information and advice - I may look into having Acer help me restore my laptop.

Thanks,
Lster

---

### Post by simcher on 2007-12-12
bro, try holding alt+F10 when booting up, i heard the ACER salesman told me if anything wrong try doing a restore by holding alt+f10, they will get information from the hidden recovery partition to restore your vista...

---

### Post by AgentZ86 on 2007-12-22
Right but, Dell has the same things, only if you deleted your restore patition this will not do anything anymore. cause the restore partition is gone now.
Just FYI on this subject I would suspect this subject is now complete to conclude after deleting the restore partition, you now need either re-installation disk from the manufacturer, New Vista installation Disks, or manufacturer will provide either new hard drive with Vista pre-installed to factory specs..



> **simcher said:**
> bro, try holding alt+F10 when booting up, i heard the ACER salesman told me if anything wrong try doing a restore by holding alt+f10, they will get information from the hidden recovery partition to restore your vista...

---

