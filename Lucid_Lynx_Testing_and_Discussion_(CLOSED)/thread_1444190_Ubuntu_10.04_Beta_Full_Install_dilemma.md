---
title: "Ubuntu 10.04 Beta Full Install dilemma"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by =CrAzYG33K= on 2010-03-31
Okay.. Here's my dilemma. I've been using UNIX / Linux for some time now, but must say I'm not a full-fledged user. I'm more of a Windows/LINUX dual-boot person.

Okay. I've been using Ubuntu in virtual machines until now (mostly coz' of losing a HDD after I couldn't uninstall Ubuntu waay waay back :o). Honestly, the virtual-machine experience has been crappy at best. No option of fancy gfx and heavily unreliable at times. I want to go full-fledged now. What has been stopping me is the fear of uninstalling Ubuntu properly, if at a later point in time I choose to get away with LINUX.. 

So forum, answer this :

1. Do I go the WUBI way ('Doze user ;)) ? I hear uninstalling Ubuntu is not a PITA then..
2. Or do I go the manual way ? I may need help with the partitioning and stuff if I choose this route..

---

### Post by uRock on 2010-04-01
I would recommend going the full install route over the Wubi route any day. I have removed ubuntu and wrote over it with NTFS using an ubuntu LiveCD running the GParted tool to delete the ubuntu partitions and create the NTFS.

Before getting started there are different step to partitioning depending on which version of Windows you are using.

---

### Post by =CrAzYG33K= on 2010-04-01
Ok, I'll be running this on a notebook alongside Windows 7.

So, the best route would be to use a partitioning manager like gParted? How do I safely uninstall Ubuntu, if I do it this way (without leaving any kind of footprint at all?)

---

### Post by uRock on 2010-04-01
> **=CrAzYG33K= said:**
> Ok, I'll be running this on a notebook alongside Windows 7.

So, the best route would be to use a partitioning manager like gParted? How do I safely uninstall Ubuntu, if I do it this way (without leaving any kind of footprint at all?)

To safely uninstall Ubuntu, you can boot a ubuntu LiveCD and use GParted within it to delete ubuntu's partitions, then install lilo to the MBR and then it will boot flawlessly to WIndows 7.

Do not use GParted to alter your Windows 7 partition. Use the Device Manager within Windows to shrink it.

---

### Post by =CrAzYG33K= on 2010-04-01
> **iRock said:**
> 
Do not use GParted to alter your Windows 7 partition. Use the Device Manager within Windows to shrink it.

You're starting to worry me :o

I was thinking of using the 'Install' icon on the desktop once you boot into Ubuntu (10.04 Beta 1) using the liveCD. And probably using the Guided Setup. Does this use gParted? I seriously do not want to mess anything up...

I thought I'd shrink my Windoze partition from there. Oh, and btw, I'm thinking of using both Win 7 and Ubuntu from my C:\ partition..

---

### Post by uRock on 2010-04-01
> **=CrAzYG33K= said:**
> You're starting to worry me :o

I was thinking of using the 'Install' icon on the desktop once you boot into Ubuntu (10.04 Beta 1) using the liveCD. And probably using the Guided Setup. Does this use gParted? I seriously do not want to mess anything up...

I thought I'd shrink my Windoze partition from there. Oh, and btw, I'm thinking of using both Win 7 and Ubuntu from my C:\ partition..

If you have a copy of the repair disk for Windows handy, then yes you can use the ubuntu installer to shrink the Windows partition.

The only way you can install both within the C drive is by installing with Wubi.

---

### Post by =CrAzYG33K= on 2010-04-01
> **iRock said:**
> If you have a copy of the repair disk for Windows handy, then yes you can use the ubuntu installer to shrink the Windows partition.

The only way you can install both within the C drive is by installing with Wubi.

Oh ****. I saw this coming. Ok, I'm stuck with WUBI then.

Is there an easy way of uninstalling Ubuntu if I go the WUBI route?

---

### Post by Sef on 2010-04-01
Moved to Lucid.

---

### Post by shindou01 on 2010-04-01
> **=CrAzYG33K= said:**
> Oh ****. I saw this coming. Ok, I'm stuck with WUBI then.

Is there an easy way of uninstalling Ubuntu if I go the WUBI route?

yes...If you use WUBI to install it from within Windows 7, you can just uninstall it like any other applications from the control panel....and you'll be just fine....

---

### Post by Herman on 2010-04-01
> Do not use GParted to alter your Windows 7 partition. Use the Device Manager within Windows to shrink it.:D Hello and excuse me for butting in here, but I'm doing some research on this subject. 
Do you have any links to any bug reports or links to threads where there is actually any documented evidence of GParted or the partitioner in the Ubuntu installer damaging an NTFS file system or moving the NTFS partition without being told to?

Thanks for any info you can provide,
Regards, Herman :)

---

### Post by uRock on 2010-04-01
> **=CrAzYG33K= said:**
> Oh ****. I saw this coming. Ok, I'm stuck with WUBI then.

Is there an easy way of uninstalling Ubuntu if I go the WUBI route?

To do a full install would require making a new partition.

Wubi is supposed to remove its boot interruption select menu when Wubi is uninstalled. Best of luck which ever way you decide to go.

Herman, are you on IRC?

---

### Post by uRock on 2010-04-01
> **Herman said:**
> :D Hello and excuse me for butting in here, but I'm doing some research on this subject. 
Do you have any links to any bug reports or links to threads where there is actually any documented evidence of GParted or the partitioner in the Ubuntu installer damaging an NTFS file system or moving the NTFS partition without being told to?

Thanks for any info you can provide,
Regards, Herman :)

That is what I have been told for the past year, so that is what I have been recommending.

Cheers,
Ronnie

---

### Post by Herman on 2010-04-01
K, thanks :)

---

### Post by Scott82 on 2010-04-01
One thing to know..... which really shouldn't affect many people at all, but could definetly affect a lot in the linux comunity..... for some reason, OEM Windows 7 install discs will not recognize the fact that the bootloader has been changed. so if you get rid of your ubuntu partition at some point, no more booting untill you reinstall windows. i'm not sure what discs in all are affected by this, but i know i had that problem with mine (64-bit home premium bought on release day). I think it has to do with how the bootloader for 7 works.... it seems that it likes to make a boot partition but instead of flagging it bootable, seems to have another bootloader on the mbr that (may or may not) points to it. so when you run the repair to reinstall the bootloader it'll just tell you that the bootloader doesn't show any errors, and won't install it.

the way i fixed this: luckily i had tried out the (not so) new feature (if you used any good versions of some previous versions of windows) that makes a decent backup with system image and all hdd files. so i reinstalled Windows, then ran the restore with the backup i had made. didn't lose much of anything 'cuz it was backing up every sunday and i got rid of ubuntu on a monday.

there are easy workarounds for this all though.... such as a usb boot disc or whatever people use for those nowdays. 

really i dono how the windows 7 boot process works now, but it's annoying. when i tried to repair it, it just told me that the last 2 times the bootloader ran it suceeded thus it must be fine, there was no [this damn thing is broken i tell yas!] button to click to force it to reinstall it.

:D

fyi, i'm a nub and this could all be inacurate... that's just what my experience was.

---

### Post by =CrAzYG33K= on 2010-04-01
Guys, Ubuntu 10.04 kicks ***.. 
I loaded up the latest WUBI build and it's all been smooth now.

Rock on, forum! :popcorn:

-- This was posted from Ubuntu 10.04 ;)

---

### Post by Herman on 2010-04-01
Thanks, Scott82.
Yes, I used to find it easier to re-install when I first started with Linux too. It doesn't hurt Windows to have a clean re-install, but it does take time to get all the files and settings back to the way you like them I imagine. 

When you only had Windows 7 in the computer, there was code in the MBR to make it go to the Windows boot sector and the Windows boot sector has code which contains the information about which sector number to look in for the boot loader. It's something like a relay race.

When you installed Ubuntu it changed the code in the MBR to make the MBR point to GRUB files in the Ubuntu partition and boot GRUB.
From GRUB you could then choose between Ubuntu or Windows.

If you chose Windows, GRUB would point to the Windows boot sector and chainload it to start the Windows boot loader and start Windows.

When Ubuntu was deleted, GRUB is also deleted because it was inside Ubuntu. 
You need to re-install code in the MBR to make it point directly to the Windows boot sector again.
The Windows 7 disk automatically repairs the internal parts of the Windows boot loader but to install a new MBR code you need to open a recovery console and run bootrec /fixmbr.

Here's a thread all about this subject, [B][HOW-TO restoring XP and Vista Bootloader & Restoring GRUB]("http://ubuntuforums.org/showthread.php?t=740221") :D
[/B]

---

