---
title: "can't boot XP after installing Ubuntu 8.04"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by drweside on 2008-06-24
I'm about to give up on dual-booting, if I can't figure this out. Hopefully, someone can give me some ideas.

I've got one HD with XP on it. It has only one partition, occupied by XP. I used PartitionMagic to resize this partition, leaving 40GB of free space at the end. When installing Ubuntu, I use the "Guided... contiguous free space" option. Ubuntu installs without any errors and I can boot into it without any problems, but I can't boot XP. I keep getting an error saying "Windows could not start because the following file is missing or corrupt: <Windows root>\system32\ntoskrnl.exe. Please re-install a copy of the above file."

Fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5193c75f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14357   115322571    7  HPFS/NTFS
/dev/sda2           14358       19214    39013852+  83  Linux
/dev/sda3           19215       19457     1951897+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dd1e688

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24792   199141708+   7  HPFS/NTFS

---------------------------------------------------------------------
---------------------------------------------------------------------
Menu.lst:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=81688f3b-21bd-4b4e-8df9-7859f3c8baa2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=81688f3b-21bd-4b4e-8df9-7859f3c8baa2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

--------------------------------------------------------------------
--------------------------------------------------------------------
Boot.ini:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect



I need XP for a few essential applications, otherwise I'd make a complete switch. Please, can someone help?

---

### Post by niyonk on 2008-06-24
> **drweside said:**
> 
timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

I had the same prob, I cant remember exactly but i think the partition(1) is supposed to be partition(0)
Try and tell us :)

---

### Post by Kobalt on 2008-06-24
If the problem remains, you can retrieve your corrupted ntoskrnl.exe file from your Windows CD. To do so, boot Windows in recovery console, insert your Windows CD in your d: drive, and proceed this way:
```
C:\Windows>cd system32
C:\Windows\system32>del ntoskrnl.exe
C:\Windows\system32>copy d:\i386\ntoskrnl.ex_
C:\Windows\system32>rename ntoskrnl.ex_ ntoskrnl.exe
C:\Windows\system32>exit
```
**Attention:** this operation may be risky for your windows install.

---

### Post by niyonk on 2008-06-24
> **drweside said:**
> 
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
**root		(hd0,0)**
savedefault
makeactive
chainloader	+1



Sorry, I did notice rather that your menu.lst might me wrong
Try 0,3   OR 0,2
It seems Grub is pointing at the wrong partition.
Try both...

---

### Post by drweside on 2008-06-24
> **Kobalt said:**
> If the problem remains, you can retrieve your corrupted ntoskrnl.exe file from your Windows CD. To do so, boot Windows in recovery console, insert your Windows CD in your d: drive, and proceed this way:
```
C:\Windows>cd system32
C:\Windows\system32>del ntoskrnl.exe
C:\Windows\system32>copy d:\i386\ntoskrnl.ex_
C:\Windows\system32>rename ntoskrnl.ex_ ntoskrnl.exe
C:\Windows\system32>exit
```
**Attention:** this operation may be risky for your windows install.

I've already tried this. Thanks for the suggestion.

---

### Post by drweside on 2008-06-24
> **niyonk said:**
> Sorry, I did notice rather that your menu.lst might me wrong
Try 0,3   OR 0,2
It seems Grub is pointing at the wrong partition.
Try both...

I'm at work right now, so I'll have to wait until later to try it. I think you're onto something, though. Considering that the linux partitions are all pointing to hd(0,1)(not hd(0, 2)) and the XP entry says hd(0, 0) and chainloader +1. Wouldn't that make the XP partition's entry point hd(0, 1)? Forgive my bootloader ignorance.

---

### Post by niyonk on 2008-06-24
> **drweside said:**
>  Forgive my bootloader ignorance.
lol

It's OK. Sometimes Ubuntu Installation is to blame
Do tell us if it works :)

---

### Post by jimv on 2008-06-24
No no, it's got nothing to do with Grub if Windows is popping up an error about missing files.  If Grub wasn't looking at the right partition, he wouldn't be getting any Windows errors...because Windows wouldn't be booting at all.  The grub partition is always 1 less than what fdisk shows...so sda1 should be hd0,0, sda2 should be hd0,1 ... etc, etc.

His boot.ini looks fine and grub looks fine.  It's probably problem with the actual file.

Try these steps instead...I don't think you can do a direct copy of the file off the xp disk:
[LIST=1]
[*]Insert the Microsoft Windows XP CD. Note: If you have a recovery CD or a restore CD and not a Microsoft Windows XP CD it is likely the below steps will not resolve your issue.
[*]Reboot the computer, as the computer is starting you should see a message to press any key to boot from the CD. When you see this message press any key.
[*]In the Microsoft Windows XP setup menu press the R key to enter the recovery console.
[*]Select the operating system you wish to fix, and then enter the administrator password.
[*]Type expand d:\i386\ntoskrnl.ex_ c:\windows\system32  <--it's not going to be D:, since you have a second HD.  It'll be E:
[*]You will then be prompted if you wish to overwrite the file type Y and press enter to overwrite the file.
[*]Type exit to reboot the computer.
[/LIST]

Also, let me know if this doesn't work...I'll post a copy of the file from my xp partition onto my site and email you a link.  It could be that your cd is SP1 and you have SP2 or something like that, and the file is different.

EDIT:
This is probably a no, but is there a WINDOWS folder on your second HD?

---

### Post by drweside on 2008-06-24
jimv,

No, there is no Windows folder in the second HD.

---

### Post by jimv on 2008-06-24
> **drweside said:**
> jimv,

No, there is no Windows folder in the second HD.

Oh well, I was thinking perhaps it would be a situation where Windoze was for some reason reading boot files off the wrong drive.

---

### Post by drweside on 2008-06-25
> **jimv said:**
> Oh well, I was thinking perhaps it would be a situation where Windoze was for some reason reading boot files off the wrong drive.

While doing some more surfing, I came across 
[this.]("http://ubuntuforums.org/showthread.php?t=485661") He's got the same MB I've got and, unless this guy has figured out what the problem is, I may have to look at the super grub disk.

---

### Post by jimv on 2008-06-25
Well, if we can't get Grub to work, then perhaps you can try loading Linux and Windows with the Windows XP bootloader.  To get the XP bootloader back, you just need to run hte fixmbr tool on the XP disk.

Then this guy has some instructions on getting the XP bootloader to load Linux:

[http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/](http://bkpavan.wordpress.com/2008/04/02/how-to-boot-linux-using-windows-bootloader-xp/)

---

