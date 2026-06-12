---
title: "Help!!  Can't boot from the cd"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by keri13 on 2007-06-17
My computer is not letting me boot through any cd.  Is there a way to install Ubuntu without having to boot?

---

### Post by logos34 on 2007-06-17
You can install straight from hard disk without the need for a bootable cd.  Starts a network install. This link works great:

[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29)

Get [DAEMON Tools]("http://www.daemon-tools.cc/dtcc/download.php") so you can mount the 'buntu iso without having to burn it to CD.

Note: make sure to get all your paths and file names correct or else it may throw you an error about windows 'notskrl' (which  should have nothing to do with it).

---

### Post by keri13 on 2007-06-17
I did as was suggested and wasn't sure which version to download.  I tried a few different ones and each time this message came up when I rebooted and tried to install:

Try (hd0,0) NTFS:
GRLDR is compressed
Try (hd0,1) Non-MS: Skip
Try (hd0,2) Non-MS: Skip
Try (hd0,3) Non-MS: Skip
Try (fd0): Invalid or null
Error

Am I missing a step or do you know which file I should download?

---

### Post by logos34 on 2007-06-17
Assuming you're on Win XP and not 98,

Try using [COLOR="Blue"]initrd[/COLOR] and [COLOR="Blue"]linux[/COLOR] from the feisty instead of dapper archive:

> [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

Extract** grldr** and **menu.lst** from the most recent .zip (4.2):               
> [http://sarovar.org/project/showfiles.php?group_id=320&release_id=767](http://sarovar.org/project/showfiles.php?group_id=320&release_id=767)

Also, make sure that 'linux' in C:\boot\grub does not have a '.htm' extension (may be hidden).  If the icon is showing up with your browser symbol (Firefox or IE) and not simply a blank, then it has the extension, whether visible or not. Either rename it by taking off the .htm or change the menu.lst entry thus:

> title Install Ubuntu
kernel   (hd0,0)/boot/linux**.htm** vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   (hd0,0)/boot/initrd.gz


The '(hd0,0)' assumes windows C:\ is first partition on first disk.  Make it match boot.ini entry for windows --> if boot.ini shows '...rdisk(1)partition(1)\WINDOWS', then replace with '(hd[COLOR="Blue"]1[/COLOR],0)'

hope that helps

edit: error says 'GRDLR is compressed' -- you must have just copied it.  You need to right click on it and 'extract here'

---

