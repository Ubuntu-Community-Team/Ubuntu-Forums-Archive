---
title: "Dual Boot with XP (Linux Already Installed)"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by Renzakuken on 2011-12-07
Hi everyone

Newbie to Linux here; briefly let me recap as to why I've decided to become a Linux User! I own an ASUS EeePC 100HA and decided that my version of XP was too slow and no where stream lined enough. I decided to format the Hard Drive and start again. This i did, proceeded to download, burn and instal Linux and here I am today. 
However, as expected, a lot of the programs I used on Windows are not compatable with Linux (Duh!), such as Syncplicity. So I decided to try and dual boot with Windows XP; following this guide [http://bit.ly/4rPdkn]("http://bit.ly/4rPdkn") I've managed to get up to stage 2 before getting stuck. I obviously need to backup GRUB prior to installing Windows however this is the output from Terminal when I try to follow the instructions:
 
```
****@ASUS:~$ sudo gedit /boot/grub/menu.lst
[sudo] password for ****:
 
(gedit:2243): Gtk-WARNING **: Attempting to store changes into '/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/recentl
 
(gedit:2243): Gtk-WARNING **: Attempting to y-used/.xbel.G6HL5V'; No such file or directory permissions of '/root/.local/share/recently-used.xbel', but failed: No such file or directly"
```
 
 
Any help with this would really be appreciated!
Kind Regards Renz

---

### Post by darkod on 2011-12-07
First of all, what version of ubuntu did you install? And did you do any upgrades to another version since, or you still have the original installed?

---

### Post by Renzakuken on 2011-12-07
I believe I have the newest version (11.10) and yes not long ago I connected to the net and updated it by way of the "Check for Updates" button on the bottom right hand side of the "System Info" Screen.
 
Renz

---

### Post by darkod on 2011-12-07
Ok, there is no need to specifically backup anything for grub2. But you will need the ubuntu 11.10 cd to restore grub2 later. If you post the result of:
sudo fdisk -l (small L)

I can give you the commands to run later to restore grub2 (after the installation of XP overwrote it on the MBR).

---

### Post by fantab on 2011-12-07
> **Renzakuken said:**
> Hi everyone

Newbie to Linux here; briefly let me recap as to why I've decided to become a Linux User! I own an ASUS EeePC 100HA and decided that my version of XP was too slow and no where stream lined enough. I decided to format the Hard Drive and start again. This i did, proceeded to download, burn and instal Linux and here I am today. 
However, as expected, a lot of the programs I used on Windows are not compatable with Linux (Duh!), such as Syncplicity. So I decided to try and dual boot with Windows XP; following this guide [http://bit.ly/4rPdkn](http://bit.ly/4rPdkn) I've managed to get up to stage 2 before getting stuck. I obviously need to backup GRUB prior to installing Windows however this is the output from Terminal when I try to follow the instructions:
 
Any help with this would really be appreciated!
Kind Regards Renz

First of all the guide you have followed is OLD, it describes GRUB LEGACY. Ubuntu has since moved to GRUB2 and Grub2 does not have menu.lst. Hence the error. 

Instead of Backing up you can also use your Live CD to restore GRUB2 after you have completed your windows install. [Read Here for more instructions]("https://help.ubuntu.com/community/WindowsDualBoot").

---

### Post by Renzakuken on 2011-12-07
Right ok so all I'd need is the Ubuntu start up disk... =S 
(I almost wrote in (small L) not off to a good start =D
 
[sudo] password for ****
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cbf2b
 
   Device Boot                 Start                End               Blocks      Id      System
/dev/sda1  *                  2048     319591375        155249664      83      Linux
/dev/sda2             310503422     312580095            1038337        5      Extended
/dev/sda3             310503424     312580095            1038336      82      Linux swap / Solaris
 
Disk /dev/sdb: 7458 MB, 7458144256 bytes
255 heads, 63 sectors/track, 906 cylinders, total 14566688 sectors
Units = sectors of 1 * 512 bytes / 512 bytes
I/O size (minimum/optimal) 512 bytes / 512 bytes
Disk identifier: 0x0217934c
 
   Device Boot                 Start                End               Blocks      Id      System
/dev/sdb1   *                    63       14566683          7283312+        b    W95 FAT32
 
 
 
Please be aware Win95 was an attempted instal prior to Linux that simply didn't work, when I get access to XP i'll be sure to remove it ;)

---

### Post by fantab on 2011-12-07
> **Renzakuken said:**
> Right ok so all I'd need is the Ubuntu start up disk... =S 
(I almost wrote in (small L) not off to a good start =D

Also, Remember Windows will NOT boot from Logical Partition, you MUST install it to Primary Partition only. (It may work but definitely not recommended).

---

### Post by Renzakuken on 2011-12-07
If i read my guide correctly Windows will convert the active Linux partition to inactive?

---

### Post by fantab on 2011-12-07
> **Renzakuken said:**
> If i read my guide correctly Windows will convert the active Linux partition to inactive?

Ideally, when dual booting, it is recommended that you install Windows first and to the first partition which should be a Primary Partition to avoid issues later. If reinstalling Ubuntu is an option then I recommend that you start over with Windows first and then Ubuntu.  

Like the Wise say, "keep it simple" and stay away from avoidable workarounds.

---

### Post by Renzakuken on 2011-12-07
Sounds like an idea, I guess, I've come this far so I wouldn't mind pressing on ;)

---

### Post by darkod on 2011-12-07
Another thing going for a complete reinstall (windows and then ubuntu again) is that right now ubuntu is taking the whole hdd. You can shrink it, and it would probably work out fine, but there is always the risk of thing going wrong.
As said earlier, if you can reinstall it's the easier way.

Don't forget one important thing: DO NOT let the XP install take the whole disk. When you reach the partitioning step, it would show the size of the ubuntu partitions although it can't recognize what they are. You will have to delete all of them, and create one new ntfs for XP. By default it suggests the WHOLE DISK. Change the value to the size you want to allocate to XP.

If you let XP take the whole disk, you have to resize right away to make space for ubuntu and XP doesn't like resizing very much.

On another note, the fdisk shows that your ubuntu root partition is /dev/sda1, the bigger one (the small one is the swap partition).
If you needed to reinstall grub2 back to the MBR from live mode in terminal, you would run:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Note that if you start all over now and install XP first as discussed, the number of the ubuntu partition after you install it again will probably change, most likely to 5. In the above command (the first one) you just replace the '1' with '5'. Or what ever your root partition is. The rest is the same. If we are talking about a single disk marked as /dev/sda. :)

Those two commands reinstall grub2 to the MBR of your disk /dev/sda from live mode.

---

### Post by Renzakuken on 2011-12-07
Okay I'll try to re-instal windows ;) Thank you for all your help guys, another newbie pushed back out to sea! 
 
Renz

---

