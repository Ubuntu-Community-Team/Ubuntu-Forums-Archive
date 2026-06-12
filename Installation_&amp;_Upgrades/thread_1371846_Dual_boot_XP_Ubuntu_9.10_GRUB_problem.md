---
title: "Dual boot XP Ubuntu 9.10 GRUB problem"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by Ragnarook7 on 2010-01-03
I used to have, on my pc, a windows XP (media center) installed. Recently I wanted to install Ubuntu 9.10 to try how Linux was (better later than never), so I did it, everything went all right. I installed Linux without problem and run it very well from grub, but when I tried to boot windows xp from grub, the screens turns completely black and the only way to get out of that was rebooting the computer. If anyone knows how to fix it (exhaustively detailed if it can be, as I'm a newbie) I would be very greatful.

I put here what appears when I tip sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3efd3ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31263   251120016    7  HPFS/NTFS
/dev/sda2           31264       36483    41929650    5  Extended
/dev/sda5           31264       36263    40162468+  83  Linux
/dev/sda6           36264       36483     1767118+  82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33676254

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    6  FAT16

Thanks a lot!

---

### Post by lmarmisa on 2010-01-03
Type this other command:

```

sudo update-grub2

```

and post the result of this command.

Best regards,

Luis

---

### Post by Ragnarook7 on 2010-01-03
Here it is

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows XP Media Center Edition on /dev/sda1
done

I hope that would help

---

### Post by lmarmisa on 2010-01-03
Everything looks good.

Are you able to boot XP now?

---

### Post by Ragnarook7 on 2010-01-03
No, I don't, but when I insert Windows xp cd and use repair option (r) and tip bootfix and mbrfix (or something like that), when I reboot computer, then it boots windows xp directly without opening GRUB, and obviously without leting me choose to boot Ubuntu.

---

### Post by lmarmisa on 2010-01-03
Did you install previously Windows Vista or Windows 7 in the partition where Ubuntu is installed now?

---

### Post by Ragnarook7 on 2010-01-03
Nope, never had any of them

Edit: I'm going to sleep, tomorrow starts the second round of Me vs Grub xD

---

### Post by lmarmisa on 2010-01-03
Dual boot Ubuntu/XP systems are very common (my PC, for example) and normally they boot fine.

I have no experience with XP Media Center, but I suppose that its differences with XP HE or XP Pro are minimal.

Try to type theses 3 commands in your system and compare the differences:

```

lmarmisa@UBUNTU910ENG:~$ **sudo mount /dev/sda1 /mnt**

lmarmisa@UBUNTU910ENG:~$ **ls -l /mnt**
total 295297
-rwxrwxrwx 1 root root         0 2009-11-22 22:18 AUTOEXEC.BAT
drwxrwxrwx 1 root root         0 2009-11-26 00:39 $AVG
-rwxrwxrwx 1 root root       211 2009-11-22 23:57 boot.ini
drwxrwxrwx 1 root root      4096 2010-01-03 21:27 Config.Msi
-rwxrwxrwx 1 root root         0 2009-11-22 22:18 CONFIG.SYS
drwxrwxrwx 1 root root      4096 2009-11-22 22:25 Documents and Settings
-rwxrwxrwx 1 root root         0 2009-11-22 22:18 IO.SYS
-rwxrwxrwx 1 root root         0 2009-11-22 22:18 MSDOS.SYS
-rwxrwxrwx 1 root root     47564 2009-11-22 23:53 NTDETECT.COM
-rwxrwxrwx 1 root root    250048 2009-11-23 01:43 ntldr
-rwxrwxrwx 1 root root 301989888 2010-01-03 21:58 pagefile.sys
drwxrwxrwx 1 root root      8192 2009-11-23 23:06 Program Files
drwxrwxrwx 1 root root         0 2010-01-03 21:03 $RECYCLE.BIN
drwxrwxrwx 1 root root         0 2009-11-22 23:21 RECYCLER
drwxrwxrwx 1 root root      4096 2009-11-23 00:05 System Volume Information
drwxrwxrwx 1 root root     69632 2010-01-03 21:45 WINDOWS

lmarmisa@UBUNTU910ENG:~$ **cat /mnt/boot.ini **
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
lmarmisa@UBUNTU910ENG:~$ 


```

$AVG directory is used by the AVG antivirus. So, this is not important for the differences.

---

