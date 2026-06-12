---
title: "How can I fix my NTFS partition?"
date: 2013-02-05
forum: Installation &amp; Upgrades
---

### Post by mikesena on 2013-02-05
Hi All,

In attempting to shrink my NTFS drive to a smaller size, so I can dual boot my currnet Windows 7 with a brand new Ubuntu 12.10 (didn't want to use Wubi), I've somehow managed to stuff up the drive and what Windows can see.

Essentially, after shrinking it with a partition manager, Windows blue screens upon restarting.  I shrank it while Windows was running (which is valid to my surprise, according to many Windows 7 & 8 dual boot HOW-TOs), and it said to restart to finish off the process.

Other partition managers I burnt to an ISO say it's a raw format.  Ubuntu *trumpets blare* to the rescue; the live CD said I can see your NTFS partition sure no problem.

SO.  Here's my issue.  I'd like to recover my drive, so that Windows can boot again.  Whether I then format or not, I'd like to get Windows running so I can do things like run steam and properly back-up... run other programs that can't just be copied over.

**How do I fix my NTFS partition from an Ubuntu Live CD?**

I've tried so far:[LIST][*] ntfsfix /mount/point/31415: Runs & exits fine; have tried with all parameters
[*] ntfs-label /mount/point/34154 NEW_LABEL: Said sure no problem.  Hasn't helped.
[*] fsck /mount/point/3115: Said it can't find/run fsck.ntfs.  I can't find that package either.[/LIST]
Help would be greatly appreciated!! :)  I'll update this description with clarifications as they come.

---

### Post by collisionystm on 2013-02-05
Ubuntu will not be able to properly repair your NTFS drive. It is using NTFS-3G which is a compatible enough to function and read the drive, but not manipulate it the way you need it to.

You will need to repair your windows installation with your Windows disk. Does your blue screen say what file is actually missing? Can you boot into safe mode? To get to safe mode, rapidly tap the F8 key either immediately after the BIOS, or selecting Windows from ubuntus boot menu.

---

### Post by mikesena on 2013-02-05
> **collisionystm said:**
> You will need to repair your windows installation with your Windows disk. Does your blue screen say what file is actually missing? Can you boot into safe mode? To get to safe mode, rapidly tap the F8 key either immediately after the BIOS, or selecting Windows from ubuntus boot menu.

Unfortunately Windows doesn't even register there's an installation there, nor does it detect it as being a NTFS drive.

I've tried to use the Windows 7 recovery tools, including running chkdsk over the drive, but it doesn't mount it, nor can it browse it.

---

### Post by collisionystm on 2013-02-05
> **mikesena said:**
> Unfortunately Windows doesn't even register there's an installation there, nor does it detect it as being a NTFS drive.

I've tried to use the Windows 7 recovery tools, including running chkdsk over the drive, but it doesn't mount it, nor can it browse it.


Ah.. thats because the windows Master Boot Record is no longer there. When you installed Ubuntu, GRUB overwrote the MBR.
The windows disk checks the MBR the the existence of a windows installation.

Well, here is what I would do.

Try safe mode
Read the blue screen to see what info you can pull from it to diagnose whats happening

Make a windows live cd. Google it.
You can boot Windows XP from the cd rom and repair the ntfs partition from there.
You will probably need a windows machine to make the disk so hopefully you have a friend or another computer

---

### Post by mikesena on 2013-02-05
> **collisionystm said:**
> Ah.. thats because the windows Master Boot Record is no longer there. When you installed Ubuntu, GRUB overwrote the MBR.

I haven't actually installed Ubuntu yet; I'm only running off the live CD.  Windows **DOES** attempt to boot, but it then blue screens during the start-up process.  I'll try and read it tonight, but as usual, blue-screens are too fast & flicker.

> The windows disk checks the MBR the the existence of a windows installation.

Well, here is what I would do.

Try safe mode
Read the blue screen to see what info you can pull from it to diagnose whats happening

Make a windows live cd. Google it.
You can boot Windows XP from the cd rom and repair the ntfs partition from there.
You will probably need a windows machine to make the disk so hopefully you have a friend or another computer

Have another laptop I can try and make this with, but I'm hoping there's another way I can recover the boot information.  I'm surprised it gets as far as it does, it comes up with the logo and starts the orbs swirling etc. then blue screens.

---

### Post by collisionystm on 2013-02-05
Have you attempted Safe Mode?

---

### Post by mikesena on 2013-02-05
> **collisionystm said:**
> Have you attempted Safe Mode?

Haven't as I'm at work currently... I'll try that later.  I'm not getting my hopes up about that :P  Would rather it be that Windows 7 recovery disk can see the installation.  Think safe mode won't pick up the files on the disk.

---

### Post by NobleYorkshire on 2013-02-05
I don't know if I am reading this right--but your MBR got deleted when you shrunk the NTFS partition with partition manager while running Windows 7? And you did not install Ubuntu?

---

### Post by mikesena on 2013-02-05
> **NobleYorkshire said:**
> I don't know if I am reading this right--but your MBR got deleted when you shrunk the NTFS partition with partition manager while running Windows 7?

No idea.  I suspect the MBR is corrupted or deleted, or something.  But I'm curious as to why it comes up with 'RAW' format in some partition managers... slash.. Windows 7 installation utilities.

> And you did not install Ubuntu?
Haven't yet; its what shrinking the drive down was going to allow.  I'm using the Live CD at the moment to copy files off the drive.  No idea why Ubuntu picks up that it's a NTFS partition but other things can't seem to.

---

### Post by darkod on 2013-02-06
First, it would help to specify which software you used to shrink the partition. The built in Disk Management? Or third party?

With windows it's usually normal to "start" the shrink operation while it's running, because that's the only way you can open programs (it has no live mode). But that only creates a sort of script, it then tells you to reboot and actually does the shrinking while windows is not running.

If it didn't do its job properly out of what ever reason, the partition table is probably messed up. If it is, chkdsk can't help much because it doesn't even see a partition to check, as you said it reports RAW format.

I agree that ubuntu tools for NTFS can rarely help in this situation. Even if they do, windows might still not like that.

What you can do from ubuntu live mode is download and run a program called Testdisk which scans the disk for partitions that existed earlier and in many cases can restore them back. You have a step by step here:
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

VERY IMPORTANT: Testdisk can help much, and also mess it up much more! If you don't understand it, ask before doing any actions. I suggest you first do the Deeper Search, post the screenshot of it which will show all old partitions found (including ones you might have deleted on purpose), and then we can see what can be done.

---

### Post by furything on 2013-02-06
Just a quick question.
You only tried to resize the windows 7 partition - a big partition?
You did not touch a partition called system reserved about 100mb???

From ubuntu live can you run in a terminal 
```
sudo fdisk -l
```
and post results here so we can see how the disk is partitioned

---

### Post by Vinay Kumar D on 2013-02-06
> **mikesena said:**
> Hi All,

In attempting to shrink my NTFS drive to a smaller size, so I can dual boot my currnet Windows 7 with a brand new Ubuntu 12.10 (didn't want to use Wubi), I've somehow managed to stuff up the drive and what Windows can see.

Essentially, after shrinking it with a partition manager, Windows blue screens upon restarting.  I shrank it while Windows was running (which is valid to my surprise, according to many Windows 7 & 8 dual boot HOW-TOs), and it said to restart to finish off the process.

Other partition managers I burnt to an ISO say it's a raw format.  Ubuntu *trumpets blare* to the rescue; the live CD said I can see your NTFS partition sure no problem.

SO.  Here's my issue.  I'd like to recover my drive, so that Windows can boot again.  Whether I then format or not, I'd like to get Windows running so I can do things like run steam and properly back-up... run other programs that can't just be copied over.

**How do I fix my NTFS partition from an Ubuntu Live CD?**

I've tried so far:
[LIST]
[*] ntfsfix /mount/point/31415: Runs & exits fine; have tried with all parameters
[*] ntfs-label /mount/point/34154 NEW_LABEL: Said sure no problem.  Hasn't helped.
[*] fsck /mount/point/3115: Said it can't find/run fsck.ntfs.  I can't find that package either.
[/LIST]
Help would be greatly appreciated!! :)  I'll update this description with clarifications as they come.




I faced same problem while installing ubuntu.
Boot using WindowXp cd.. continue till partition process, soon after partition-exit the setup... Your memory will be back.

---

### Post by darkod on 2013-02-06
> **Vinay Kumar D said:**
> I faced same problem while installing ubuntu.
Boot using WindowXp cd.. continue till partition process, soon after partition-exit the setup... Your memory will be back.

First, the OP didn't even start installing ubuntu. This was done by the windows partitioning program.

Second, if you start the windows installer and write new table/partitions, you will lose all data on the disk even if you don't continue installing XP. The OP doesn't want that.

---

### Post by Mark Phelps on 2013-02-06
> **Vinay Kumar D said:**
> I faced same problem while installing ubuntu.
Boot using WindowXp cd.. continue till partition process, soon after partition-exit the setup... Your memory will be back.

The OP said they are using Win7.  You do NOT want to mess around with Win7 filesystem partitions using an XP CD.

To the OP: What you can try (which probably will not work -- but you never know) is using a Windows PC to download and burn the Minitool Partition Wizard Boot CD.  Boot from that and see if it will let you select the Recover Partition option -- and if that works, you should be OK.

---

### Post by collisionystm on 2013-02-06
> **Mark Phelps said:**
> The OP said they are using Win7.  You do NOT want to mess around with Win7 filesystem partitions using an XP CD.

To the OP: What you can try (which probably will not work -- but you never know) is using a Windows PC to download and burn the Minitool Partition Wizard Boot CD.  Boot from that and see if it will let you select the Recover Partition option -- and if that works, you should be OK.


Unless you know something I don't, there is no reason that windows XP cannot safely manipulate a windows 7 partition. The NTFS file system structure has not changed in a very long time.

---

### Post by mikesena on 2013-02-07
> **darkod said:**
> First, it would help to specify which software you used to shrink the partition. The built in Disk Management? Or third party?
I can't remember the name of it... I could find the link.  Yes to using Windows first though.

> What you can do from ubuntu live mode is download and run a program called Testdisk which scans the disk for partitions that existed earlier and in many cases can restore them back. You have a step by step here:
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

VERY IMPORTANT: Testdisk can help much, and also mess it up much more! If you don't understand it, ask before doing any actions. I suggest you first do the Deeper Search, post the screenshot of it which will show all old partitions found (including ones you might have deleted on purpose), and then we can see what can be done.

Thanks!  Will try TestDisk tonight.

---

### Post by mikesena on 2013-02-07
> **furything said:**
> Just a quick question.
You only tried to resize the windows 7 partition - a big partition?
You did not touch a partition called system reserved about 100mb???

From ubuntu live can you run in a terminal 
```
sudo fdisk -l
```
and post results here so we can see how the disk is partitioned

At work so I can't paste the error, but there was a problem running this.  Complained about being able to list for some reason.  Will paste the results later.

---

### Post by furything on 2013-02-07
> At work so I can't paste the error, but there was a problem running  this.  Complained about being able to list for some reason.  Will paste  the results later.     Try running up gparted or disk utility and post a screen shot or the partitions.

I know a bit late as we need to get windows working again first but is this a desktop?
instead of using a single hard drive (if desk top) you could install a second hd and have that for linux.
Similarly for a laptop you could install (as opposed to live boot) a usb stick.

---

### Post by Mark Phelps on 2013-02-07
> **collisionystm said:**
> Unless you know something I don't, there is no reason that windows XP cannot safely manipulate a windows 7 partition. The NTFS file system structure has not changed in a very long time.

Actually, YES it did.  MS made some changes to NTFS when Vista came along and continued with Win7.  I found out the hard way when I created an NTFS partition using GParted for a Vista install, and repeatedly had filesystem failures after that.  I blew that away, recreated it with Vista -- and there were no problems after that.

The article below lists some NTFS changes: 

[http://technet.microsoft.com/en-us/library/ff383236%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/ff383236%28v=ws.10%29.aspx")

---

### Post by collisionystm on 2013-02-07
> **Mark Phelps said:**
> Actually, YES it did.  MS made some changes to NTFS when Vista came along and continued with Win7.  I found out the hard way when I created an NTFS partition using GParted for a Vista install, and repeatedly had filesystem failures after that.  I blew that away, recreated it with Vista -- and there were no problems after that.

The article below lists some NTFS changes: 

[http://technet.microsoft.com/en-us/library/ff383236%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/ff383236%28v=ws.10%29.aspx)


  > I found out the hard way when I created an NTFS partition using GParted

Why would you use a linux tool to create an NTFS file system? You created it using NTFS-3G. NTFS-3G is an opensource NTFS compatible tool made so linux can read an NTFS drive. I would never trust Gparted to safely create a stable NTFS partition. 
That being said, XP can create an NTFS partition a million times better than Gparted.

---

### Post by oldfred on 2013-02-07
I also found out that there are differences. And chkdsk from Windows 7 on a XP partition will convert it.

I used a Windows 7 repair CD to run chkdsk on my XP partition. It did find additional errors. But it converted the NTFS PBR - partition boot sector to the new version. In Testdisk you can compare (dump) the backup PBR to the active PBR and in plain text was bootmgr (for Vista/7) on current and ntldr (for my XP) on backup. I had to restore backup. 
Or you can use the "bootsect.exe /nt52 c:" command to restore an XP PBR.

---

### Post by mikesena on 2013-02-07
So!  I gave up on the whole thing and after buying a new external drive and backup the data, went to install Windows again fresh (still need to dual boot).  Windows **STILL** couldn't pick up the drive.  That's when I got suspicious.

[LIST=1]
[*]I went into gparted (eyeballs above conversation)
[*]Deleted the mount that I'd attempted to create in Windows
[*]**RE**sized  the drive *back* to what it was before.
[*]Rebooted.
[*]Windows asked whether I wanted to recover Windows (instead of booting normally)
[*]THIS TIME, it actually seemed to do something.
[*]Rebooted, and all was well.
[/LIST]

Thanks to the advice from all.  Turns out even undo'ing what you've done with *partitions* can sometimes fix issues.

---

