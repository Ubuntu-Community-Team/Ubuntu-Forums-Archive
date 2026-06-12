---
title: "Uninstalling"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by Downtown on 2005-09-11
Is there any way to uninstall/reinstall Ubuntu from a hard drive?  I tried booting off the CD to reformat and reinstall the OS from scratch, but it won't boot the CD.  I also tried to add my Ubuntu HD to a WinXP system, and though the system detects the drive, it doesn't give me any access to it, so I don't even know its drive letter to fdisk it.  If you need more info to help me, let me know. Thx in advance for your help.

Oh, and plz don't ask why, I just want to.

---

### Post by mlomker on 2005-09-11
There wouldn't be a drive letter in windows.  You'd just go into the control panel, computer management, and then delete the disk partition.

Regardless, you'll need to figure out why your machine won't boot to a CD or you won't be able to reinstall it anyway.  Either the disc is bad (assuming other discs will boot) or you have to go into your PC's BIOS at boot-up and set the CD to be bootable.

---

### Post by Downtown on 2005-09-13
[QUOTE=mlomker]There wouldn't be a drive letter in windows.  You'd just go into the control panel, computer management, and then delete the disk partition.

Regardless, you'll need to figure out why your machine won't boot to a CD or you won't be able to reinstall it anyway.  Either the disc is bad (assuming other discs will boot) or you have to go into your PC's BIOS at boot-up and set the CD to be bootable.[/QUOTE]
My Control Panel doesn't have computer management in XP, so I can't delete the partition that way.  How could I start to figure out why my CPU won't boot a CD.  I tried 4 different copies of the Ubuntu install disk, and none would work.  I went into the BIOS and told it to boot from CD, and it didn't work.  Any other ideas?

---

### Post by mlomker on 2005-09-14
[QUOTE=Downtown]My Control Panel doesn't have computer management in XP, so I can't delete the partition that way.  How could I start to figure out why my CPU won't boot a CD.  I tried 4 different copies of the Ubuntu install disk, and none would work.  I went into the BIOS and told it to boot from CD, and it didn't work.  Any other ideas?[/QUOTE]

Usually there's a place in the BIOS where you can select the 'boot order'.  Are you saying that you put the CD-ROM drive before the hard disk?

---

### Post by Downtown on 2005-09-15
[QUOTE=mlomker]Usually there's a place in the BIOS where you can select the 'boot order'.  Are you saying that you put the CD-ROM drive before the hard disk?[/QUOTE]
 Yes.  I even set it so that the CD is the only thing that would boot, but it still didn't.  I'll try a few more things, then I'll report back.

---

### Post by agm642 on 2005-09-15
If you have more than one CD drives, try putting the disk in another one. Also, you can usually access System Management by right clicking My Computer and then selecting it.

---

### Post by Downtown on 2005-09-18
[QUOTE=agm642]If you have more than one CD drives, try putting the disk in another one. Also, you can usually access System Management by right clicking My Computer and then selecting it.[/QUOTE]
 Ok, so I put the Ubuntu hard drive as part of my Windows system.  Then I went into Computer Management and deleted the partitions.  Then I set up my computer so that all I have on IDE is the Ubuntu HD (at this point hopefully empty), and my DVD-RW drive (which I would set as the bootable drive).  I did, and the CD would still not boot.  So I've come to the conclusion that my DVD drive isn't compatible with Ubuntu, or maybe Linux altogether.  Is there any site where I can check my hardware compatibility?

---

### Post by mlomker on 2005-09-18
> So I've come to the conclusion that my DVD drive isn't compatible with Ubuntu, or maybe Linux altogether.

You haven't said anything that makes me think this is a linux issue.  You can't boot a Windows XP CD in that machine, either, can you?  If you can then the Ubuntu CD is bad, that's all.

---

### Post by Downtown on 2005-09-19
[QUOTE=mlomker]You haven't said anything that makes me think this is a linux issue.  You can't boot a Windows XP CD in that machine, either, can you?  If you can then the Ubuntu CD is bad, that's all.[/QUOTE]
Well, I don't have a bootable XP disk to check that with, but I've tried many copies of the CD.  I didn't burn them, Ubuntu shipped them to me and I used one of them to install Ubuntu on the HD on a different computer which I don't have anymore.

---

### Post by mlomker on 2005-09-20
>  Ubuntu shipped them to me and I used one of them to install Ubuntu on the HD on a different computer which I don't have anymore.

Then it's your machine and you'll need to keep looking at it.  If you're living on a University campus then it shouldn't be hard to find a nerd to give you a hand.   :smile:

---

### Post by MrCheese on 2005-09-20
[QUOTE=Downtown]Is there any way to uninstall/reinstall Ubuntu from a hard drive?  I tried booting off the CD to reformat and reinstall the OS from scratch, but it won't boot the CD.  I also tried to add my Ubuntu HD to a WinXP system, and though the system detects the drive, it doesn't give me any access to it, so I don't even know its drive letter to fdisk it.  If you need more info to help me, let me know. Thx in advance for your help.

Oh, and plz don't ask why, I just want to.[/QUOTE]

If you put the drive in your XP box & run fdisk there should be 5 options, the fifth being  to select a hdd. Make sure you pick the correct one!!!!! Beware that sometimes M$ systems won't play with partition schemes from linux so you may have to boot a rescue cd to do so, unless you have Partition Magic or similar.

You really need to check why the cd won't boot first or you will be stuck for re-installation. Make sure you haven't set the bios to boot hdd before cd, if that's ok the cd may be dud & you need to burn a new one.

---

### Post by Downtown on 2005-09-20
Well, I put the disk in my XP box (which is actually also my Linux box depending on which drives I connect), and I deleted the Ubuntu partitions through Computer Management.  I don't know why the CD won't boot, or else I wouldn't be here.  I do set the CD to boot first.  I even set it to be the only thing to boot, but it won't work.

---

### Post by Downtown on 2005-09-23
Ok, I can get the Live CD to boot, as I am running in it right now, but I still can't get the Install disk to boot.  I keep getting Error 17 when I do.  Any ideas?

---

### Post by Downtown on 2005-09-28
Not that anybody cares anymore, but I got the install disk to work.  I sat down and messed with a bunch of settings in the BIOS and it booted, I formatted, and installed.  I'm not using it too much cuz most of my school stuff requries Winblows, but I'm gonna get into it once I get a bigger HD for Windows after which I'll put Ubuntu on the drive I currently use for Windows.

---

