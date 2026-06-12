---
title: "Grub Error 21"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by zizzu on 2007-02-01
Thanks for your help in advance. As you've guessed, I'm a newbie to Linux installations. I'm not a new user though & am fairly comfortable with unix but not when it comes to Grub Errors..:) 

I have a Toshiba Tecra Windows XP laptop & a external 40GB Seagate Drive. I tried installing Mandriva One 2007 (can I still use this forum?) using the live CD onto to my external drive. Mandriva was installing on the external drive (it created the partitions by itself) but when it came to setting up Grub, I keep getting the error 21 at Stage 1.5. I don't have a copy of /etc/fstab but this is what my partitions look like.

Laptop HDD (37GB)
-----------
Device: sda1
DOS drive letter: C
Type: NTFS
Size: 34GB

Device: sda2
DOS drive letter: D
Type: Hidden W95 FAT32 (LBA)
Size: 2.9GB

External Seagate (40GB)
----------------
Device: sdb1
Type: Journalised FS: ext3
Size: 7.8GB
Mounted

Device: sdb5
Type: Linux swap
Size: 3.9GB
Mounted

Device: sdb6
Type: Journalised FS: ext3
Size: 25GB
Mounted

I installed Mandriva on sdb1. Below is what the /boot/grub/menu.lst file looks like.

timeout - 10
color black/cyan yellow/cyan
default 3

title linux
kernal (hd0,0)/boot/vmlinuz root=/dev/ splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title linux-nonfb
kernal (hd0,0)/boot/vmlinuz root=/dev/
initrd (hd0,0)/boot/initrd.img

title failsafe
kernal (hd0,0)/boot/vmlinuz root=/dev/ failsafe
initrd (hd0,0)/boot/initrd.img

title windows
root (hd0,0)
makeactive
chainloader +1

title windows1
root (hd0,1)
makeactive
chainloader +1

When asked where to install GRUB, I selected the internal drive on my laptop where XP is installed. I suppose that's the MBR. Now, the only thing I can do with my laptop is boot it up with Madriva with the live CD. Any suggestions? Is there some edit I need to make to the menu.lst file? May be pointing to the wrong disc? Please let me know if you need additional info. I've searched lots of forums but can't seem to come up with a clear answer on what needs to be done. Thanks again.

---

