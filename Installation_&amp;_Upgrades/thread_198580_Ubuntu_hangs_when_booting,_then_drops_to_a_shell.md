---
title: "Ubuntu hangs when booting, then drops to a shell"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by Oxide on 2006-06-17
Hello everybody.
I've been using Ubuntu since Hoary with no problems until I decided to go for Dapper.
Since I've got everything partitioned the way I like it from the older versions I usually just reformat the root partition and install fresh into that instead of upgrading.

I used the alternate installation disk and the text based install (just what I'm used to). The install goes fine without any hickups whatsoever, BUT when I reboot and choose Ubuntu (I have a dual boot)  it does the following:

Booting 'Ubuntu, kernel 2.6.15-23-386
root (hd0,1)
Filesystem type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/sda2 ro quiet splash
         [Linux-bzImage, setup=0x1c00, size=0x15774d]
initrd /boot/initrd.img-2.6.15-23-386
         [Linux-initrd@0x87c000, 0x673fd2 bytes]
savedefault
boot
uncompressing Linux ... Ok, booting the kernel.


Then I get the Ubuntu "splash" screen with the progress bar and beneeth it I get the following:

Loading essential drivers... ok
Mounting root file system...
Waiting for root file system...


The system hangs like this for a few minutes and then it gives the following message:


Alert! /dev/sda2 does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter ´help´ for a list of built-in commands.

/bin/sh: can't access tty; job control turned off





Does anybody know what is going on? 
Like I said, I've been running Hoary and Breezy just fine with the exact same setup.

Thanks!

---

### Post by Oxide on 2006-06-18
I've browsed the forums a lot and found the problem.

Ubuntu was trying to boot from the wrong disk. This seems to be a problem for quite a lot of users and this thread had all the info I needed:

[http://www.ubuntuforums.org/showthread.php?t=186115]("http://www.ubuntuforums.org/showthread.php?t=186115")

To cut a long story short I managed to find out what the disks were called by booting Ubuntu in safe mode and read what disks it was seeing.

Then I rebooted, pressed "e" in the GRUB menu, pressed "e" again and changed my disks from sda2 to sdc2. Then pressing "Enter" and "b" to boot.

Then I was able to boot into the terminal and I had to change /etc/fstab and /boot/grub/menu.lst accordingly.

When I upgraded from 386 to 686 I had to go through this all over again, but now it works just fine.

---

### Post by Ted_Smith on 2006-06-19
Oxide has summarised it nicely. 

I've also written a [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=197956&highlight=ALERT%21") last weekend which has a bit more detail especially for those with multiple IDE's.

---

