---
title: "Installation to USB Pen? (NOT Live USB)"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by jingaling on 2012-11-12
Hey guys,

I have a work laptop that I use at home occasionally but it runs Windows 7. What I would like to do is buy a 64GB USB pen and install Ubuntu 12.04 on to that so I can boot my work laptop to the USB pen and basically have a 'machine' with me at all times.

Am I right in thinking that it would simply be the same as installing to any HDD? Or is there something special I need to do?

To be clear, I don't want a live USB with persistence, I want a fully working installation of Ubuntu 12.04 running from a USB pen. I've tried searching the forums but it's just coming back with Live USB threads.

Thanks all!

Kev

---

### Post by cwsnyder on 2012-11-12
> **jingaling said:**
> Am I right in thinking that it would simply be the same as installing to any HDD? Or is there something special I need to do?

To be clear, I don't want a live USB with persistence, I want a fully working installation of Ubuntu 12.04 running from a USB pen. I've tried searching the forums but it's just coming back with Live USB threads.The major problem with _installing_ to a USB pen instead of using a Live install with persistence is that GRUB will want to always have the same devices and partitions installed as were present at grub-install, or grub-install will have to run again.  If you are _only_ going to use the pen-drive with your work laptop, this would work.  If you want to keep a full working environment which can go to other computers, you want a Live install with persistence.

---

### Post by jingaling on 2012-11-12
Thanks for the quick reply. I'd be happy to go for persistence but I've only ever seen it go as big as 4GB. Is it possible to make a persistent drive for the whole 64GB?

---

### Post by cwsnyder on 2012-11-12
You can use the rest of the drive for persistence, or use some of it for data storage accessible either from Windows or Linux, if it is formatted FAT32.

---

### Post by jingaling on 2012-11-12
Ah yeah, that makes sense actually. So I could have two FAT32 partitions, one of say 4GB and the other 60GB. I then have 4GB (or so) for apps so I could install dropbox on the persistence drive then tell it to look at the other partition for the folder.

Thanks for the help.

---

### Post by majnoon on 2012-11-12
I done it for a broken netbook for my sister I installed it inside of VMware and installed it to pen drive acting like it was a regular hard drive ,it seems to be running ok

---

### Post by oldfred on 2012-11-12
I have a full install in my 16GB flash drive with 8GB for / and 8GB for data.

It is just like a full install, but you have to use manual install to get the choice on where to install grub2's boot loader. I turn off os-prober, so it does not find my many installs on my hard drives and then add a few boot entries in 40_custom for those I might want to boot.

You do need to make a few settings to reduce writes similar to a SSD drive. If you want encryption you have to use alternative installer and it will be LVM which adds complexity.

Some suggest the lighter weight versions so they load faster, but once loaded into RAM the flash drive is no different, RAM caches the most recent activity so if you have 4GB of RAM or more it works well, except for writes.

 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)
With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by C.S.Cameron on 2012-11-12
You can have persistent ext2, 3 or 4, partitions named casper-rw and casper-home, of any size that will fit the drive.
Casper-rw stores your downloaded programs and casper-rw stores your settings, email and downloads, etc. *I've included a FAT32 or NTFS partition for transferring files between computers, but you can use the root partition for this, if you wish.

Here is a step by step:

Boot Live CD.
Plug in flash drive.
Start Partition Editor, (gparted).
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Startup Disk Creator", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk and delete the casper-rw file.
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by ercherramon on 2012-11-12
I have a full install of Ubuntu 10.04 on a flash drive of 16 GB. I made it from an Ubuntu LiveCD. Just be careful and enough patience creating the correct partitions. You create a primary partition with Gparted for the system and an extended partition for the Home and the swap area. when formatting EXT4 Partitions, sure to put in the formatting option: round cylinders in order to have a good partition table and the end of the Ubuntu installation process, you must choose the boot sector or partition GRUB on sdb or your pendrive and not on your hard drive because you will modify the MBR of your hard disk.

---

