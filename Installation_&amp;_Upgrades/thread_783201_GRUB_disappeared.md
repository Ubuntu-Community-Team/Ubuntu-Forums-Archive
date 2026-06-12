---
title: "GRUB disappeared"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by amyhughes on 2008-05-05
I have Ubuntu 8.04 installed on the same drive as my WinXP installation, and for about a week I was able to boot either. Grub was used to offer a choice of OS to load, and I had WinXP as my default OS.

Today I do not get the menu. Grub does not load during booting. It just boots right into Windows. There is no menu and there is no countdown that has gotten too short and I am not just not seeing it. Grub never appears at all.

1. Is there a way to restore my boot loader without destroying the Ubuntu partition?

2. Any idea how this happened?

Thanks,
Amy

---

### Post by uberlube on 2008-05-05
Grab SUPERGRUBDISK and burn it to cd. Boot it a startup and it will give you the options to boot intio either Win or Linux and also has grub repair options. Hopefully this will help.

---

### Post by amyhughes on 2008-05-05
> **uberlube said:**
> Grab SUPERGRUBDISK and burn it to cd. Boot it a startup and it will give you the options to boot intio either Win or Linux and also has grub repair options. Hopefully this will help.

Thank you, I gave it a try. I was able to restore my boot menu, but none of the selections work.

If I try to boot windows I get this:

Starting up ...
NTLDR is missing
Press Ctrl+Alt+Del to restart

If I try to boot Linux I get this:

Error 22: No such partition
Press any key to continue...

The only SGD option that does anything remotely useful is the one that restores Windows as the boot OS, and that's how I'm able to boot the machine. But that's pretty much where I started from.

---

### Post by Rohen on 2008-05-21
I have the same problem, except I've tried all options: 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and I still can't boot into Ubuntu :(

Any idea what else I could  do?

---

### Post by louieb on 2008-05-21
Use a live CD you can use Ubuntu or my favorite for this type of thing [Knoppix Linux]("http://www.knoppix.net/"). You can browse around your hard drive just to see if things look right.   

Now you need to get to get a GRUB command prompt and let it do it work. Here's one of the best  explanations I have found .
[IDBS Restore Grub w/LiveCD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") 

Ubuntu's own Herman explains in detail just what you have to do to get GRUB up and running again. Good Luck.

---

### Post by Rohen on 2008-05-21
> **louieb said:**
> Ubuntu's own Herman explains in detail just what you have to do to get GRUB up and running again. Good Luck.

Wow that's quite a lot of info... I'll give it a go.  THANKS!

BTW - just to release some stress by typing... I've tried the live CD/terminal approach but I keep getting an Error 12: Invalid.... when I type: setup (hd0)

I'm in Windows now so I can't upload an image of the text that appears...

---

### Post by louieb on 2008-05-22
Probable cause of the error 12 is not issuing the **root (hd0,#) **command first.  ( the # part being the  partition # GRUB has its files in).

GRUB is pretty complex almost a small operating system itself. Its a 3 step process Herman describes.

the short of it is.

[LIST=1]
[*]use the **find** command to get the the partition # where GRUB lives.
[*]use the **root **command to  set the GRUB root partition.
[*]then finally use the** setup** command to  place GRUBS setup (stage1) code in the MBR or a partitions boot sector.
[/LIST]

Go through the examples (your partition numbers my vary) and   you should get GRUB working again. If not I have more questions about your setup. 
Lou.

---

### Post by Rohen on 2008-05-22
Hi Lou,

Ok I've tried that with no success.  I'm running Hardy and XP on the same HD of 60 GB, Ubuntu has 30 GB and XP 20 GB.  I've read Herman's guide on how to re-install grub but I have no idea why I keep getting error 12.  Steps I take:

>grub
>find /boot/grub/stage1
 (HD0,5)
>root (hd0,5)
>setup (hd0,5)
 (I'll try and post error 12 text when I get home...)

I've even gone as far as installing a Boot manager software for windows... when I boot I can choose between XP and Linux (finally shows Linux) but for some reason Linux doesn't start up after I choose it.  It just hangs.  XP boots fine.

I'm writing this from WINDOWS :S :mad:

---

### Post by louieb on 2008-05-22
Rohen, From what you said in your last post there is no good reason for it not to work.  That should have setup GRUB so that it cam be chainloaded form another boot loader. 
The **setup (hd0,5)** should have put the stage 1 code in the boot sector of the 2nd logical partition.  Then your other boot loader should have been able to transfer control to GRUB.   If you wanted to boot straight to GRUB then the command should have been **setup (hd0**).

If you have internet with the live CD. Post your partition table. to do that
Open Applications>accessories>terminal and run
```
sudo fdisk -l
```Does this PC have 2 hard drives 1 sata and 1 ide drive. The reason I'm asking this is sometimes GRUB  can get confused. But it can be corrected.

---

### Post by Rohen on 2008-05-26
Hi!  Thanks for helping.  No it only has one HD.  I'll try and post the fdisk -l outcome soon :(, reason is that now sometimes the boot just hangs and Windows doesn't even want to boot, I can't even go into my BIOS!!!  I can't run the risk of not having a PC I need to work.

No idea what happened but I think I should just re-install everything :( :( :(... Just as long as I can recover some files from Ubuntu...

Anyone know how I can do that with the Live CD?  Sometimes it says I don't have enough permission...

:confused:

---

### Post by louieb on 2008-05-26
From what you described sounds like you have hardware problems. May be something simple like the CMOS battery.  OR more serious like the hard drive or motherboard. 

To get the data off with the live CD, look in the places menu, the hard drives partitions should be listed there. Click on the Ubuntu partition. You should be able to use Nautilus to copy your data off to an external drive. 

If you run into a permission problem try pressing Alt+F2 and key **gksudo nautilus**  then press enter.    

See what kind of hard drive it has in it and go to the manufactures website. Most have some sort of diagnostic utility the you can download  to check the drive.  Good Luck.

---

### Post by Rohen on 2008-05-29
Hey louieb thanks for helping me out.  I used "gksudo nautilus" and now I can access the files in my Ubuntu Install from LiveCD but I still can't move them over to my USB so that I can reinstall everything...

sudo fdisk -l gives me this:

```
omitting empty partition (5)

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cf18342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2819    22643586    7  HPFS/NTFS
/dev/sda2            2820        7301    36001665    5  Extended
/dev/sda3            6999        7301     2433816   82  Linux swap / Solaris
/dev/sda5            2820        6820    32137969+  83  Linux
/dev/sda6            6821        6998     1429753+  82  Linux swap / Solaris
```

Now when I try the find /boot/grub/stage1 it says::confused:
Error 15: File not found

---

