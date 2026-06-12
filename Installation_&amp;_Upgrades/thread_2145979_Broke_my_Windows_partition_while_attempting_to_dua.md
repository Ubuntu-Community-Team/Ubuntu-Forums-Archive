---
title: "Broke my Windows partition while attempting to dual boot, please help me fix"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by jwei92 on 2013-05-17
****Windows 7 Professional****


****Ubuntu 12.10****


While trying to set up dual boot, I chose the first option in the Ubunutu by accident that said "Replace Windows 7". Out of panic, after I saw something along the lines of "writing partition", I pulled the plug on my computer (most likely, an AWFUL idea).


Now, I cannot boot into Windows (which I expected) and my startup disk can neither detect the (partition?) or Operating System. If I boot normally, my computer tells me 


DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER


Please, tell me what to do, if anything is possible.

---

### Post by fantab on 2013-05-17
Do you have Windows recovery/repair or Windows install media? 
Boot you Ubuntu Disk and "Try Ubuntu"... open Gparted and post the screen-shot of your Disk Partitions.

---

### Post by Mark Phelps on 2013-05-17
What you CAN do depends on what you HAVE...

You probably did not make an image backup of Win7 before you did the Ubuntu install, so you have no backup to use for restoration.

If your PC came with Win7 preloaded, and it has a way to launch a Restore (which would be explained in the documentation that came with it) -- AND -- you did not mess around with the Recovery partition in any way, you might be able to restore Win7 that way.

Otherwise, you can try recovering the Win7 partitions using a Windows tool -- Minitool Partition Wizard.  We highly recommend this on the Win7 forum, not just because it's free, but because it works quite well. You would have to download the ISO file, burn that to CD, boot from that, and see if the Partition Recovery option works.

If that fails, then your only recourse would be to use a Windows utility to recover what files you have and do a reinstallation.

---

### Post by jwei92 on 2013-05-17
> **Mark Phelps said:**
> What you CAN do depends on what you HAVE...

You probably did not make an image backup of Win7 before you did the Ubuntu install, so you have no backup to use for restoration.

If your PC came with Win7 preloaded, and it has a way to launch a Restore (which would be explained in the documentation that came with it) -- AND -- you did not mess around with the Recovery partition in any way, you might be able to restore Win7 that way.

Otherwise, you can try recovering the Win7 partitions using a Windows tool -- Minitool Partition Wizard.  We highly recommend this on the Win7 forum, not just because it's free, but because it works quite well. You would have to download the ISO file, burn that to CD, boot from that, and see if the Partition Recovery option works.

If that fails, then your only recourse would be to use a Windows utility to recover what files you have and do a reinstallation.

[B]Just for some updates:
[/B]Windows does NOT detect an OS under Repair Tools.
Using bootrec /scanos produces the message "Zero Windows Operating Systems detected"
Using startup repair after setting the main partition with diskpart gives me an "error that cannot be automatically fixed. System volume on disk is corrupt"
Message during boot to windows has now changed to "Missing operating system"

My latest backup was pre-[creating files I desire to re-acquire]. My PC did not come with Windows 7 preloaded, as far as I'm aware (I installed my own hard drive). Also, I do NOT think I messed around with the recovery partition (I am not sure if I have one, as a matter of fact).

My main concern is to recover a handful of files from the hard drive if possible, then I'm fine with reinstalling windows.

---

### Post by fantab on 2013-05-17
When you installed Ubuntu and instructed the installer to 'replace Windows', it formatted the HDD to suit Ubuntu, by the time you powered off its was late.

Like Mark suggests, [Minitool Partition Wizard]("http://www.minitool-partitionrecovery.com/") may help you recover that lost partition and the files you need. Give it a try. If that doesn't help then consider [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

Good Luck...

---

### Post by jwei92 on 2013-05-17
So Ubuntu formatted pretty quickly then huh...

I presume with minitool I need another PC? Connect my HDD to it, and then use Minitool?


[http://i.imgur.com/GqVOcj2.jpg](http://i.imgur.com/GqVOcj2.jpg)
[http://i.imgur.com/LW7RTCL.png](http://i.imgur.com/LW7RTCL.png)

---

### Post by fantab on 2013-05-17
Either that or [use MiniTool bootable CD]("http://www.partitionwizard.com/partition-wizard-bootable-cd.html"). With respect to TestDisk, you can install it on Ubuntu install Disk and use it.

sudo apt-get install testdisk

---

### Post by Mark Phelps on 2013-05-17
If you want to recover some files and you're willing to spend some money, and can connect the drive to a Windows PC, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by jwei92 on 2013-05-17
This worked like a wonder. I 'restored' my NTFS partition, repaired it with the WinRE, and now, it is working again. I can boot and log-in.

Now please, can someone give me a guide on how to install Ubunutu 12.10 AFTER Windows is already installed? I ask this because the install menu only has replace, and no side-by-side.

---

### Post by Mark Phelps on 2013-05-17
No side-by-side generally indicates that the maximum of 4 primary partitions already exists on the drive -- and the installer is thus prevented from creating any more.

You would do better starting a new thread asking for installation assistance -- as this one deals with repairing Windows.

---

