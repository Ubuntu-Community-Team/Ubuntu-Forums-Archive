---
title: "cant find NTLDR, cant boot vista"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by dennisros on 2008-03-05
Hi, been searching for a solution a while but cant seem to fix it.
I dual boot vista and linuxmint, with vista installed first.
In the beginning I couldn't find the vista boot in grub so I added 

title           Windows Vista
root            (hd0,0)
                makeactive
                chainloader +1

this made me find Vista in grub but when I try to boot it the message "NTLDR is missing" come up. Need help to be able to dual-boot, need to get in to Vista.
Regards 
/Dennis

---

### Post by Pumalite on 2008-03-05
I need you to post:
sudo fdisk -lu

---

### Post by dennisros on 2008-03-05
Here it is

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000331a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    96243711    48120832    7  HPFS/NTFS
/dev/sda2        96245415   312576704   108165645    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfb33d98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7807589     3903763+  82  Linux swap / Solaris
/dev/sdb2         7807590    66396644    29294527+  83  Linux
/dev/sdb3        66396645   312576704   123090030   83  Linux

Regards 
/Dennis

---

### Post by Pumalite on 2008-03-05
Change this:
title Windows Vista
root (hd0,0)
makeactive
chainloader +1
To this:
title Windows Vista
rootnoverify (hd0,0)
map  (hd0,0) (hd1,0)
map  (hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

Save, exit and reboot.

---

### Post by dennisros on 2008-03-05
Thanks for the fast reply, but it still dont work, must be something wrong with the code you gave me. Now it looks like this:

## ## End Default Options ##

title 		Windows Vista
rootnoverify 	(hd0,0)
map 		(hd0,0) (hd1,0)
map 		(hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

title		Linux Mint, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

And when I try to boot, I only see something like

rootnoverify 	(hd0,0)
map 		(hd0,0) (hd1,0)
map 		(hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

up in the left corner and nothing happens. What should I do?
Regards 
/Dennis

---

### Post by Pumalite on 2008-03-05
This, you have to put below the ###END DEBIAN AUTOMAGIC KERNEL LIST:
title Windows Vista
rootnoverify (hd0,0)
map  (hd0,0)  (hd1,0)
map  (hd1,0)  (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by dennisros on 2008-03-05
Sorry, when I try to boot vista everything except for "title Windows Vista" is displayed up in left cornet and nothing happens. What is wrong? Now grub looks like this:



## ## End Default Options ##


title		Linux Mint, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Windows Vista
rootnoverify 	(hd0,0)
map 		(hd0,0) (hd1,0)
map 		(hd1,0) (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by Pumalite on 2008-03-05
Try this:
title Windows Vista
rootnoverify (hd0,0)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
makeactive
chainloader +1

---

### Post by dennisros on 2008-03-05
**No** Now its like this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000331a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    96243711    48120832    7  HPFS/NTFS
/dev/sda2        96245415   312576704   108165645    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcfb33d98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7807589     3903763+  82  Linux swap / Solaris
/dev/sdb2         7807590    66396644    29294527+  83  Linux
/dev/sdb3        66396645   312576704   123090030   83  Linux


What partitions needs to be mapped? /dev/sda1 is vista and /dev/sdb2 is / for mint.
Regards
/Dennis

---

### Post by Pumalite on 2008-03-05
Well, you have Vista in sda1 (map (hd0,0)). The problem might be in the fact that you have /swap in sdb1 (map (hd1,0)). Maybe your mapping should be:
map (hd0,0) (hd1,1)
map (hd1,1) (hd0,0)
Try that and let's see.
(it's better to have /swap at the end)

---

### Post by Pumalite on 2008-03-05
Post:
cat /boot/grub/device.map

---

### Post by dennisros on 2008-03-05
Nope nothing happens, it just stops with the same text in the upper left corner. No failure massage or nothing. Need to get this working, should I fix vista boot manager and add mint through EasyBSD (cant remember the name), how do I do that then, or do you have any other better idea.
Just would like to say thank you very much for helping me.
Regards 
/Dennis

missed you last post, here it is:

(hd0)   /dev/sda
(hd1)   /dev/sdb

---

### Post by Pumalite on 2008-03-05
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by froy02 on 2008-03-05
Your previous entries for window sda1 is (hd0,0) are the right entries so there's no need to    map to (hd0) to (hd1):
    title Windows Vista
    root (hd0,0)
    makeactive
    chainloader +1
What you need is fix the boot sector of vista to get rid of the  NTLDR missing error using bootrec.exe.  Follow the instructions to install a boot sector in the Vista partition.  Use the fixboot option of bootrec.exe so that you don't have to restore grub.
Here's the website for the instructions:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Pumalite on 2008-03-05
How did you partition? With Vista you have to allocate space for Ubuntu/Mint from WITHIN Vista with Vista's partitioner

---

### Post by dennisros on 2008-03-05
I'm going to try froy02's idea. 
I partitioned in gparted, on a empty hard drive, did I have to do something inside vista before?

---

### Post by dennisros on 2008-03-05
I cant seem to get to the Recovery Options, It says that I should do like this:

1.	Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.	Press a key when you are prompted.
3.	Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.	Click Repair your computer.
5.	Click the operating system that you want to repair, and then click Next.
6.	In the System Recovery Options dialog box, click Command Prompt.
7.	Type Bootrec.exe, and then press ENTER.

Bet when I put in my vista cd, I only get to the stage where I should choose which partition I would like to install Vista on, and says when I pick one that all data will be stored in windows.old. How do I find the Recovery Options so that I can do a Bootrec.exe?

---

### Post by Pumalite on 2008-03-05
You can fix your Vista MBR with Super Grub too:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by jimv on 2008-03-05
Follow this guy's instructions:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Then once you have Vista back up and running, reinstall GRUB.  You can do that with a SuperGrub CD.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by froy02 on 2008-03-06
> **dennisros said:**
> I cant seem to get to the Recovery Options, It says that I should do like this:

1.	Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.	Press a key when you are prompted.
3.	Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.	Click Repair your computer.
5.	Click the operating system that you want to repair, and then click Next.
6.	In the System Recovery Options dialog box, click Command Prompt.
7.	Type Bootrec.exe, and then press ENTER.

Bet when I put in my vista cd, I only get to the stage where I should choose which partition I would like to install Vista on, and says when I pick one that all data will be stored in windows.old. How do I find the Recovery Options so that I can do a Bootrec.exe?

The choice to repair Vista should be before you get to the installation part.  Do not choose install, choose repair.

---

