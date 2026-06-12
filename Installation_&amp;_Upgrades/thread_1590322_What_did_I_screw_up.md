---
title: "What did I screw up?"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by FXL5 on 2010-10-07
I'm new to this sort of thing, so best to be just factual.  I acquired:  1 Samsung N230 netbook, with Windows 7 Starter pre-installed. 1 flash drive 1 copy Ubuntu Netbook Remix. Converted the flash drive into a bootable copy of UNR. So far, so good.   Boots from USB, I go in, play a bit, decide that yes, this is fun, but I want to keep Windows. So, dual-boot. No problem, install UNR to a new, small, partition on the (single) hard drive of my netbook. Obviously, if I'm going to be dual-booting, I need GRUB. So, check my partitions (sudo fdisk -l), install GRUB to the partition and to what should be the MBR (sudo grub-install --root-directory=/dev/sda6 /dev/sda). Again, so far, so good. (Please understand, my knowledge of all this is bits and pieces put together from too many tutorials, which is, I'm sure, why I'm in the fix I'm in).   This, I believe, is where I went wrong - I decided to check it actually worked, so I shut down the netbook and turned it on again. It installed all right...I have a command prompt. I'm sure this is fantastically useful if I knew what I was doing, but it's not what I expected - I dual-boot Debian and Vista on this machine, and I get an &quot;arrow keys to select your operating system&quot; screen which works very nicely. I do recall that that screen originally just had Debian on it, and I had to edit (which file?), adding a chainload command and a pointer to the right hard drive.   TL;DR - GRUB is present, so are two operating systems, all I have is a &quot;limited&quot; command prompt. The Linux partition is sda6, the swap is sda7, and I have NO idea how to boot anything at all. What do I tell it to do, and what do I do to give myself an OS-select screen instead of a CL?   P.S - apologies for being an idiot.

---

### Post by oldfred on 2010-10-07
Welcome to the forums.

Is the command line a grub before boot or is it booting and giving you an Ubuntu command line.

Manual boot.
Manual boot:

Adjust drive, partition to your install s/b sda6 or hd0,6:
sh:grub>ls
#If on (hd1,3) or sdb3
sh:grub>ls (hd1,3)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub>initrd (hd1,3)/initrd.img
sh:grub>boot

From liveCd you can reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Sometimes simple reinstall does not work:
HOWTO: Purge and Reinstall Grub 2 from the Live CD -drs305
In cases where the boot info script results look normal, I usually recommend purging and reinstalling G2 via the LiveCD and chroot. Reinstalling may not recover a failing system if files are missing.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

IF you want to know where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by FXL5 on 2010-10-07
It's a GRUB before boot - I think this ```
Adjust drive, partition to your install s/b sda6 or hd0,6: sh:grub>ls #If on (hd1,3) or sdb3 sh:grub>ls (hd1,3)/ #Should show the links vmlinuz & initrd.img sh:grub>linux (hd1,3)/vmlinuz root=/dev/sdb3 sh:grub>initrd (hd1,3)/initrd.img sh:grub>boot
```  Is what I was after...but I don't understand what you're trying to tell me. I give it ls, it gives me a list of partitions (hd0,1-3+5-7). If I input  ```
ls (hd,X)
```  it gives me a variation on "Partition hd0,6: Filesystem type ext2 - Last modification time ..... VVID ....."  No files at all?   EDIT: Never mind, missed a / - no wonder it didn't tell me anything! Second edit - Ok, it half works. initrd.img is "file not found", despite appearing from ```
ls (hd0,6)/
``` Trying to boot anyway results in it telling me that sda6 doesn't exist, and then a kernel panic.

---

### Post by FXL5 on 2010-10-07
Ok, wow, got there in the end. I still need to work out exactly what went wrong, but here's the fix: ```
https://help.ubuntu.com/community/Grub2#METHOD 3 - CHROOT
```  Now boots everything. I'm so happy!

---

### Post by oldfred on 2010-10-07
Glad you got it working.

---

