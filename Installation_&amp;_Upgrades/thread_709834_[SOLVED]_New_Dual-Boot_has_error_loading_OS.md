---
title: "[SOLVED] New Dual-Boot has error loading OS"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by ILikeToast on 2008-02-27
Hello. 

So, when I first set up my PC, I had a 250GB sata HD. As I was installing Windows XP, I set aside a 60GB partition, to install Linux in later. 

Since then, I've added an IDE 200GB hard drive, but left it undivided, and used it for nothing but storage. 

I finally got around to installing Ubuntu 7.10 in the 60GB partition, to make it a dual-boot system. I told the LiveCD to install in the largest uninterrupted free space. About thirty minutes later, it's done. When I restart my PC, however, I get the message "Error loading OS." 

I used the LiveCD again to check up on my HDs. Both HDs, and all the files on them, are fine. I tried reinstalling the LiveCD, but now it only gives me two options: using an entire hard drive, or doing everything manually. I tried to do it manually, but it never let me entirely through the menu. Maybe I'm doing something wrong, but it's always telling me that I need to establish a root system, or something like that. 

What would be the easiest way to fix this problem? 

Thank you.

---

### Post by dstew on 2008-02-27
Boot the live CD, open a terminal, and enter the command ```
sudo fdisk -l
```Post the result to the forum. Maybe all you need to do is re-install grub, which is much easier that re-installing the whole operating system.

---

### Post by ILikeToast on 2008-02-27
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1130322c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b654b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       22886   183831763+   7  HPFS/NTFS
/dev/sdb2   *       22887       30198    58733640   83  Linux
/dev/sdb3           30199       30515     2546302+   5  Extended
/dev/sdb5           30199       30515     2546271   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by dstew on 2008-02-27
> When I restart my PC, however, I get the message "Error loading OS."It is probably trying to boot the /dev/sda1 drive. See if you can change the boot order in your BIOS to boot the /dev/sdb drive.

---

### Post by ILikeToast on 2008-02-27
It doesn't give me that option. It lets me choose between the 250GBHD, the CD-Rom Drive, and the floppy disk drive (Odd, because I don't have one).

---

### Post by dstew on 2008-02-28
Let's do this. Boot a Live CD, enter a terminal, and enter **grub**. That should get you the grub command line, with the **grub>** prompt. At the grub prompt, enter the command```
find boot/grub/stage1
```That should tell the grub-name of the partition that has the grub system and menu. Use that result as the argument in the root command:```
root (hd1,0)
```Then setup the grub boot loader in the Master Boot Record of the first disk:```
setup (hd0)
quit
```End the Live CD session, change your BIOS to boot the hard drive if you need to, then reboot. If you get the same error, try the same thing except use setup (hd1)

---

### Post by ILikeToast on 2008-02-28
On the first step you gave me, it says this: 

__________

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find boot/grub/stage1 

Error 15: File not found

grub> find boot/grub/stage1

Error 15: File not found

grub>

---

### Post by dstew on 2008-02-28
Try the same, starting grub with **sudo grub**

EDIT: Oh, sorry, the command should be ```
grub> find /boot/grub/stage1
```The / at the beginning of the path name is important.

---

### Post by ILikeToast on 2008-02-28
Okay, I tried using the **setup (hd0)**, and it didn't work. Then I tried **setup (hd1)**. 

Now I have a grub loader! 

That's the good news. The bad news is that it doesn't take me anywhere else. When I select Linux, it tells me: 

**Error 22: No such partition. **

When I select Windows XP, it tells me: 

**NTLDR is missing. **

---

### Post by dstew on 2008-02-28
OK, we are halfway there. When you get to the grub menu, move to the menu item you want to work on using the up and down arrows, and press 'e' to edit the boot statements. Use the arrows to highlight the root statement, and press 'e' again. If the root statement is (hd0,1) change it to (hd1,1). If it is (hd1,1) change it to (hd0,1). Press enter, then 'b' to boot. Hopefully you will get your Ubuntu up and running.

When Ubuntu is running, you will need to edit these same root statements in /boot/grub/menu.lst to make the change permanent. I recommend the command ```
gksudo gedit /boot/grub/menu.lst
```When you edit the linux root statement, also look up at the top of the file for the line **#groot** and change that one also. Then, when you get a kernel update, it won't scramble the roots again.

---

### Post by ILikeToast on 2008-03-01
Thanks, that works. However, Windows XP is still giving me the same error message. How can I fix that?

---

### Post by confused57 on 2008-03-01
[deleted]

---

### Post by dstew on 2008-03-01
If you are booting, good, you are done. If not, it might depend on how the Windows entry is made in /boot/grub/menu.lst. If the WIndows root is (hd1,0) you will need to use map statements to fix it. Please post to the forum the output of** sudo fdisk -l** and **cat /boot/grub/menu.lst** if you are still having problems. If no problems, then please mark the thread as solved (Thread Tools).

---

### Post by ILikeToast on 2008-03-01
**For the command "sudo fdisk -l":**

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1130322c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b654b64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       22886   183831763+   7  HPFS/NTFS
/dev/sdb2           22887       30198    58733640   83  Linux
/dev/sdb3           30199       30515     2546302+   5  Extended
/dev/sdb5           30199       30515     2546271   82  Linux swap / Solaris



**For the menu.lst:**

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6248fd72-0edc-483b-ba10-992e9cd0c3e2 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=6248fd72-0edc-483b-ba10-992e9cd0c3e2 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by dstew on 2008-03-01
That is pretty interesting. Your linux partition has the grub root (hd0,1) but the file system name sdb2. That suggests that grub is mapping /dev/sdb as (hd0). If this is true, then the windows root (hd1,0) maps to the /dev/sda1 partition, which you said was a storage partition. That is why you get the "NTLDR is missing" error. Try changing the Windows entry to```
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```That is, change the root to (hd0,0) and remove the map statements.

---

### Post by ILikeToast on 2008-03-02
Yes! Everything is working great now! Thanks for all of your help!

---

