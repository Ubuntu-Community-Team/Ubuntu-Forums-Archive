---
title: "Erased Boot Loader"
date: 2006-05-01
forum: Installation &amp; Upgrades
---

### Post by Kallid on 2006-05-01
SPECS:
Two Hds one for windows and one for ununtu.

Setup:
Windows was installed before I installed Ununtu on a second hard drive.

Problem:
I formatted my windows HD and I when I went to load Linux, it says OS not found.  I am assuming that I deleted the boot loader that was located on the windows HD.  I have no idea how to reload, the boot loader.  If someone could assist me or point me in the right direction I would appreciate it.

Thank you in advance

Raleigh

---

### Post by Sef on 2006-05-01
I think via the live cd that grub can be reinstalled.   Yes, windows wipes out grub.

---

### Post by Kallid on 2006-05-01
I fully understand the cause and the problem, but I am not sure how to reinstall the boot loader.  I have used the live CD, and I tried to setup the boot loader but it doesnt seem to do anything.

---

### Post by stoeptegel on 2006-05-01
a copy&paste from the forum somewhere which is known to work well:

> 
 Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.
 
 In other words, if you use something like Boot Magic or System Commander, the commands you've just read will overwrite what you've got.
 
 If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different. Here's are the instructions that I have for my system:
 
 How to Restore the Grub Menu after a Re-Ghosting:
 
 1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.
 
 2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.
 
 3. Type "grub" which makes a GRUB prompt appear.
 
 4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.
 
 5. Type "root (hd0,3)".
 
 6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".
 
 7. Type "quit".
 
 8. Restart the system. Remove the bootable CD.
 

Note that since ubuntu already is installed on a second disk (slave pata or second sata), that you are likely to install grub on the MBR of the first (master pata or first sata) formatted hard disk.

---

### Post by Kallid on 2006-05-01
Thank you ill try that.

---

### Post by Kallid on 2006-05-01
I reinstalled windows and found i was unable to enter ubuntu(boot loader).  

So I was told to try this:
su
grub
find /boot/grub/stage1
root (hd1,3) - whatever it spits out.
setup(hd1,3)

once I was able to get this to work; I tried to use the bootloader I get this error below.
-------------
Im getting the same error but mine says,

root (hd1,0)
File system type unknown, partition type 0x7

kernel /boot/vmlinuz-2.6.12-10-386 root = /dev/hdb1 ru quiet splash

Error 17: cannot mound selected partition
------------

---

### Post by Kallid on 2006-05-01
I reinstalled windows and found i was unable to enter ubuntu(boot loader).  

So I was told to try this:
su
grub
find /boot/grub/stage1
root (hd1,3) - whatever it spits out.
setup(hd1,3)

once I was able to get this to work; I tried to use the bootloader I get this error below.
-------------
Im getting the same error but mine says,

root (hd1,0)
File system type unknown, partition type 0x7

kernel /boot/vmlinuz-2.6.12-10-386 root = /dev/hdb1 ru quiet splash

Error 17: cannot mound selected partition
------------

---

