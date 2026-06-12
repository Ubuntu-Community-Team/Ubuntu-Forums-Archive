---
title: "Dual-boot with Ubuntu."
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by Burbruee on 2005-09-23
Hello.

First I just want to say that I really like Ubuntu and that it is probably the best dist I have ever had installed.  O:) 

Anyway, I was installing Ubuntu and was going to perform a Dual-boot between Ubuntu and WinXP.
I installed WinXP first and Ubuntu afterwards so letting GRUB "take over".
Ubuntu starts just fine, however I cannot seem to boot into my WinXP anymore.
( A sign from above not to use MS-Products maybe?  :-P )
I must still be able to boot into windows, mainly because I haven't found a working way for my Twinhan DVB-T card to work in Ubuntu, and second of all I don't have ANY discspace left since all my other drives are NTFS filesystem and so I will not be able to write, only read. ( Can, but it's too risky. I've got a lot of things I cannot afford to loose. )

When I select WinXP from GRUB I get a message that the file \System32\hal32.dll is missing.
However, I have mounted my winxp drive successfully in Ubuntu, and the file does exist.
I suspect he is trying to get the file from the wrong drive.
( In winxp before Ubuntu install my win-drive for some reason was F:\ and not C:\
He had also for some reason put some systemfiles on the root of my storage-dive and named it C:\  :roll:  )

I don't know if it helps but I post my output of fdisk -l
```

burbruee@ubuntudesktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 251,0 GB, 251000193024 byte
255 huvuden, 63 sektorer/spår, 30515 cylindrar
Enheter = cylindrar av 16065 × 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/hda1               2        1333    10699290    f  W95 Utökad (LBA)
/dev/hda2   *        2551       30515   224628862+   7  HPFS/NTFS
/dev/hda3            1334        2550     9775552+  83  Linux
/dev/hda5              2        1276    10241406    7  HPFS/NTFS
/dev/hda6            1277        1333      457821   82  Linux växling / Solaris

Posterna i partitionstabellen är inte i diskordning


``` 

The lang is swedish but I hope you can understand it anyway.
The windrive is hda5, I've tried making it bootable ( * ) but it didn't help.

---

### Post by weijie90 on 2005-09-23
hi
could u please post the contents of your /boot/grub/menu.lst? btw, its ELL-S-T, not ONE-S-T.
which WinXp partition are you trying to boot?

---

### Post by Burbruee on 2005-09-23
```



title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-custom 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-custom root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-custom
savedefault
boot

title		Ubuntu, kernel 2.6.10-custom (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-custom root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-custom
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1



```
The winxp is on /dev/hda5 as far as I know.
Not sure what you're meaning with " its ELL-S-T, not ONE-S-T "

---

### Post by ngms27 on 2005-09-23
I think the root entry for XP is wrong

Try changing it to:

root		(hd0,4)

JonnyT

---

### Post by Burbruee on 2005-09-23
[QUOTE=ngms27]I think the root entry for XP is wrong

Try changing it to:

root		(hd0,4)

JonnyT[/QUOTE]

Yeah, I've already tried that, said it couldn't boot, unknown filesystem or something like that..
Which is strange, since I mounted it successfully in Ubuntu and am able to read and check the files on the drive.
I'll try it again though, and report back the exact error message.

---

### Post by Burbruee on 2005-09-23
[quote="grub"]
root (hd0,4)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
Error 12: Invalid device requested
[/quote]

I've tried everything from (hd0,0) to (hd0,5) with no success.
I think it's because winxp for some unknown reason wrote some systemfiles to the root of another partition and made it C:\ and the actual OS got installed on F:\
Where C: = (hd0,1) and F: = (hd0,4)
If I write 0.1 in grubmenu I will get to the NT bootloader but it will make that error that system32\hal.dll is missing. 
( Because be is looking on the wrong drive most likely. )
Maybe if I could somehow change boot.ini it could work, but I can't since it is ntfs filesystem and I can only read ntfs in Ubuntu..

The following files exist on the WRONG drive ( data storage drive. ) that should exist on the windows-drive instead:

AUTOEXEC.BAT
Bootfont.bin
boot.ini
CONFIG.SYS
IO.SYS
MSDOS.SYS
NTDETECT.COM
ntldr

What to do?  :???:

---

### Post by Snowman73 on 2005-09-23
Im a bit of a n00b to this dual boot thing, but when ubuntu installation "shrinks" the windows partition does this mean that when i boot in Windows that I won't have any available disk space?

---

### Post by fordfan753 on 2005-09-23
Can youi boot XP from grub command line?

```
rootnoverify (hd0,4)
chainloader +1
boot
```

Also, I think the Windows entry in menu.lst may be wrong. I would have put

```
title         Windows XP
makeactive        (hd0,4)
rootnoverify       (hd0,4)
chainloader +1
boot
```

The makeactive bit may or may not be there...I don't completely remember.

---

### Post by Burbruee on 2005-09-23
I get:

A disc read error occured
Press Ctrl+Alt+Del to reboot.

Tried from commandline also.
With and without makeactive.

---

### Post by fordfan753 on 2005-09-23
That's strange, very strange, I have never seen that happen, and I have set up lots of Ubuntu/Windows dual boots for friends who want to try Ubuntu out, but don't want to leave the "safety" of something they know.

---

### Post by Burbruee on 2005-09-23
So no idea of what to do?
If I were to re-install winxp, it will probably take over the bootloader.. Must I also re-install Ubuntu again after that to get Grub back?

---

### Post by JimmyBEng on 2005-09-23
if you re-install win, it will retake the bootloader (at least as I understand it).  But there is a way to restore GRUB without reinstalling ubuntu. I saw it here somewhere, I'll look for it and post it if I find it.

---

### Post by JimmyBEng on 2005-09-23
Here it is.
[Restore GRUB (if your MBR is messed up)](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by Burbruee on 2005-09-23
[QUOTE=JimmyBEng]Here it is.
[Restore GRUB (if your MBR is messed up)](http://www.ubuntuforums.org/showthread.php?t=24113)[/QUOTE]
 Thanks, I'll try it out this weekend.

---

### Post by weijie90 on 2005-09-24
be sure to back up the data in your winxp drive! burn the stuff onto a cd or something. :) good luck!

---

### Post by Burbruee on 2005-09-24
[QUOTE=weijie90]be sure to back up the data in your winxp drive! burn the stuff onto a cd or something. :) good luck![/QUOTE]
 There's nothing to back up. :)
I just installed xp three days ago then I installed Ubuntu right after. ;)

---

### Post by weijie90 on 2005-09-24
[QUOTE=Burbruee]There's nothing to back up. :)
I just installed xp three days ago then I installed Ubuntu right after. ;)[/QUOTE]
 good for you!

---

### Post by Burbruee on 2005-09-25
Tried it, and got it working now. ;)

The first one ( Using the Ubuntu install-cd ) didn't work.
But using the livecd, mounting the linuxdrive and running grub-install worked just fine for me. 
Now Dual-booting is working. :)
Thanks.

---

