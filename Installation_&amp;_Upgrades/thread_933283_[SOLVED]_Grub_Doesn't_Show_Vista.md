---
title: "[SOLVED] Grub Doesn't Show Vista"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by N00bB00b on 2008-09-29
Um, Ok, so I have 8.04 on my box.  I haven't had any need to go into Vista until this morning, so I didn't even notice until this morning that...Grub doesn't have an entry for Vista.  The partitions are still there (in fact, there are annoyingly sitting right on my desktop), but no boot option.

I can boot into the recovery console that was included, but not into Vista.

What do I do to diagnose this?

TIA.

---

### Post by caljohnsmith on 2008-09-29
How about posting the following first:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by N00bB00b on 2008-09-30
**[SIZE="4"][COLOR="Red"]The meat & potatoes of fdisk:[/COLOR][/SIZE]**
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16370234     8185086   12  Compaq diagnostics
/dev/sda2   *    16370235    86654609    35142187+   6  FAT16
/dev/sda3        86654610   150159554    31752472+  83  Linux
/dev/sda4       150159555   156296384     3068415   82  Linux swap / Solaris


**[SIZE="4"][COLOR="Red"]The meat & potatoes of the grub menu:[/COLOR][/SIZE]**
title		Ubuntu 8.04.1, kernel 2.6.24-19-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=5ff7cc40-e0e4-4a2a-b204-bf40dd52d904 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.24-19-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-386 root=UUID=5ff7cc40-e0e4-4a2a-b204-bf40dd52d904 ro single
initrd		/boot/initrd.img-2.6.24-19-386

title		Ubuntu 8.04.1, kernel 2.6.15-52-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=5ff7cc40-e0e4-4a2a-b204-bf40dd52d904 ro quiet splash
initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.04.1, kernel 2.6.15-52-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-52-386 root=UUID=5ff7cc40-e0e4-4a2a-b204-bf40dd52d904 ro single
initrd		/boot/initrd.img-2.6.15-52-386

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-09-30
The only partition on your HDD that could possibly have Vista in it is sda2, but it has a FAT16 file system; did you install Vista yourself or did it come with your computer? I would just be really surprised if your computer came with Vista installed to a FAT16 partition; Vista should be using NTFS, and in fact I'm not even sure Vista would run with a FAT16 file system. Can you give some ideas of how this may have happened? 

Anyway, you can try to boot the sda2 partition and see what happens; while you are in Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom where it has your Windows entry, change it to:
```
title Windows Vista (maybe)
root (hd0,1)
savedefault
chainloader +1
```
Let me know what happens when you try to boot with the above entry.

---

### Post by Mark Phelps on 2008-09-30
Your machine shows no sign of having Vista on it -- anymore!

FAT-16 formatted partitions predate even Windows XP, which defaulted to FAT-32 format.  Vista defaults to NTFS format and, when you install it, will either reformat an existing partition to NTFS, or will create a new partition -- even then, using NTFS.  XP installation provided the option of choosing FAT-32 or NTFS; Vista does not provide that option.

Without further info, my guess is that you overwrote and reformatted your Vista partition when you installed Ubuntu.  That would explain the total absence of an NTFS partition.

---

### Post by N00bB00b on 2008-09-30
sda2 does indeed appear to be the partition that contains Windoze, based on the various things I've found in the folders (I didn't use Vista for long before installing HH.  The main plan for this box was to turn it into a testbed for HH, but I wanted to make sure I had a fallback plan in case I didn't appreciate the experience).

Anyway, the last entry in grub boots a recovery mode for Vista (sda1 is the vendor-installed recovery partition).  So, before I do this, should I instead just add another entry to grub instead?

---

### Post by N00bB00b on 2008-09-30
FYI, it should be noted that when I do the boot on sda1, it fires up XP and then the recovery tool.

I suppose option 2 would be that sda1 is the boot into the recovery console and sda2 contains the factory-installed backup image of Vista, but in sda2's Users directory appears to be the username that I created when I fired up Vista.

Anyway, back to the current question - should I instead add a new entry to grub, and what should that entry contain?

---

### Post by caljohnsmith on 2008-09-30
How about we look at what is in the sda2 partition before you go further; from Ubuntu do the following:
```
sudu umount /dev/sda2
```
Don't worry about a device not mounted error, this is just to make sure. Continue with:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
Please post the output of the above commands.

---

### Post by N00bB00b on 2008-09-30
> **caljohnsmith said:**
> How about we look at what is in the sda2 partition before you go further; from Ubuntu do the following:
```
sudu umount /dev/sda2
```
Don't worry about a device not mounted error, this is just to make sure. 
No error, fyi.  Out of curiosity, how to I keep these partitions from mounting at boot time?  I really don't need or want access to sda1 and sda2, ever.  All I'm going to do is F*** them up.



> Continue with:
```
sudo mount /dev/sda2 /mnt
ls -l /mnt
```
Please post the output of the above commands.

```
total 1563332
-rwxrwxrwx 2 root root       8013 2007-04-10 15:55 -20070410.log
drwxrwxrwx 1 root root          0 2008-08-22 15:39 Acer
-rwxrwxrwx 1 root root        166 2007-04-10 12:45 Arcade.log
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root          0 2007-04-10 11:56 Book
drwxrwxrwx 1 root root       4096 2007-04-10 11:58 Boot
-rwxrwxrwx 1 root root     438840 2006-11-02 04:53 bootmgr
-rwxrwxrwx 1 root root       8192 2007-04-10 11:58 BOOTSECT.BAK
-rwxrwxrwx 2 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 07:59 Documents and Settings
drwxrwxrwx 1 root root       4096 2007-04-10 11:56 DRV
-rwxrwxrwx 1 root root  526569472 2008-08-22 15:55 hiberfil.sys
drwxrwxrwx 1 root root          0 2007-04-10 12:36 Intel
-rwxrwxrwx 1 root root 1073741824 2008-08-22 15:55 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-08-22 15:37 ProgramData
drwxrwxrwx 1 root root       8192 2008-08-22 15:36 Program Files
drwxrwxrwx 1 root root          0 2008-08-22 15:39 $RECYCLE.BIN
-rwxrwxrwx 1 root root        284 2007-04-10 12:30 RHDSetup.log
-rwxrwxrwx 1 root root        178 2007-04-10 12:50 setup.log
drwxrwxrwx 1 root root       4096 2008-08-22 15:37 System Volume Information
drwxrwxrwx 1 root root       4096 2008-08-22 15:36 Users
drwxrwxrwx 1 root root      32768 2008-08-22 15:38 Windows
```

---

### Post by caljohnsmith on 2008-09-30
Well it's hard for me to believe, but it does look like Vista is indeed installed in sda2. Just add the Vista entry in your menu.lst that I gave in post #4, reboot, choose it from the Grub menu, and let us know what happens.

---

### Post by N00bB00b on 2008-09-30
As an interesting (and annoying) sidenote, gedit doesn't support workspaces.  I'll reboot in a moment.

---

### Post by Mark Phelps on 2008-09-30
OK ... I stand corrected ... Those are definitely Vista files, not XP.

As caljohnsmith has said, it will be interesting to see what happens when you are able to boot from that partition.

---

### Post by N00bB00b on 2008-09-30
Yep, that did it.  Vista booted just fine.  
1) It's running Vista Home Basic.  I don't know if that makes the filesystem matter.
2) This box (an Acer Aspire 3680) was really, really REALLY cheap when we bought it, even though it was brand new.  The clerk's crack at the time was "What do you want that for?  All you're going to be able to do is run Linux on it".  Well, I have to say, it runs Linux quite nicely, thank you.

Thanks to folks who helped.  Thank-you's will be going out shortly.  I'll leave this thread open a little longer before closing it.

---

### Post by caljohnsmith on 2008-09-30
> **N00bB00b said:**
> Yep, that did it.  Vista booted just fine.  
1) It's running Vista Home Basic.  I don't know if that makes the filesystem matter.
2) This box (an Acer Aspire 3680) was really, really REALLY cheap when we bought it, even though it was brand new.  The clerk's crack at the time was "What do you want that for?  All you're going to be able to do is run Linux on it".  Well, I have to say, it runs Linux quite nicely, thank you.

Thanks to folks who helped.  Thank-you's will be going out shortly.  I'll leave this thread open a little longer before closing it.
I'm glad that worked, but I'm still incredulous that some tech actually installed Vista to a FAT16 partition; I was thinking like Mark that it probably wasn't even possible, but I guess we've all been proven wrong. :biggrin:

---

### Post by Mark Phelps on 2008-09-30
Gollly .... learn something every day. Maybe that's whey they call it Vista Home "basic"!!

---

### Post by meierfra. on 2008-09-30
Just a guess, but I think it is  just a mistake in the partition table, and the filesystem is actually NTFS and not FAT16.

To test my theory, I  used "cfdisk" to change all my partition to type FAT16.  I was still still able to mount all partitions.
XP and Vista did not mind at all: They booted up just fine
But I wasn't able to boot Ubuntu anymore.

---

### Post by Mark Phelps on 2008-10-03
caljohnsmith:

Since you apparently CAN boot directly into the Windows partitions using GRUB, thought I would try your suggestions to try and fix my problem.

No success...

Please look at the following post:

[http://ubuntuforums.org/showthread.php?p=5901822#post5901822]("http://ubuntuforums.org/showthread.php?p=5901822#post5901822")

---

