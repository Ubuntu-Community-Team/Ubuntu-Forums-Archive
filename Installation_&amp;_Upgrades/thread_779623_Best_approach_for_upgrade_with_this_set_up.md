---
title: "Best approach for upgrade with this set up"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by whazooo on 2008-05-02
Hello all,

I'm running gutsy now, everything is smooth. I know I should let it be
But.... Every time I open the update manager and see the Upgrade available...:)

Anyway heres my setup,
Nvidia 7600 gs set up with envy
two sata hard drives 
Dual boot xp and of course gutsy. one on each drive
I have a separate /home directory on sbd4

What do you all think the best way to go to upgrade this setup?
Below is some system info.
Thanks!

heres the output of fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe45fe45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57de1b21

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       19314       38536   154408747+  83  Linux
/dev/sdb2           38537       38913     3028252+   f  W95 Ext'd (LBA)
/dev/sdb3               1        6563    52717266    7  HPFS/NTFS
/dev/sdb4            6564       19313   102414375   83  Linux
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order


# menu.lst - See: grub(8), info grub, update-grub(8)


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=13df3334-ce00-4f31-8183-e6d3c79b81f9 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=13df3334-ce00-4f31-8183-e6d3c79b81f9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
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

---

### Post by Sef on 2008-05-02
Best way to update is to do a clean install.  Burn a disk and install from that.  You do lose your settings though.

Update will work, but more likely to be problamatic.  

**Back up** your data first before updating.

---

### Post by whazooo on 2008-05-02
Thanks for the reply.


With a seperate /home partition and well over a hundred gig of personal data
Thats really the best method?

---

### Post by ali999 on 2008-05-02
I also suggest that you do a fresh install. You have a second hard drive, just unplug it for now or leave it untouched and set up as you would normally. Then once it is set up you can setup ubuntu to automatically mount your second disk containing all this data, and if you want, even set this disk as your /home. I recommend this because I've always heard that upgrading from Gutsy is just messy.

---

### Post by whazooo on 2008-05-02
Thanks for the reply ali999,

I understand the idea of a fresh installation, However while I do have two hard drives,
One 350 gig is xp and one is a 350 gig that holds my gutsy installation the boot loader is on hdo,0 which is the first hard drive, and holds the xp install with all my data and programs I need to run that wont run under wine or has a linux alternate.

I also Have a directories and programs under / that has over a 100 gig that I dont want touched.

I suppose I want to much for a specilized setup like mine. I just was looking for a way to just upgrade the core for LTS reasons. Over all I'm real happy with my gutsy setup and it does what I need to be productive, So I'll most likely just stay where I am for now...

Thanks all....

---

