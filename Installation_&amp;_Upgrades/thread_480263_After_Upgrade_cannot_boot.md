---
title: "After Upgrade cannot boot"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by anafshalom on 2007-06-21
I used the command 
$ gksu "update-manager -c"

I went to sleep.  In the morning the desktop was up, with a slightly new look, When I tried to reboot the system hangs.  I've tried all of the options in the grub menu and the result is the same.

Right now I've booted using the CD-Rom

1. Is there an easy fix?

2. Can I retireve my data from SATA drive before reinstalling from CD if necessary?

---

### Post by confused57 on 2007-06-21
> **anafshalom said:**
> I used the command 
$ gksu "update-manager -c"

I went to sleep.  In the morning the desktop was up, with a slightly new look, When I tried to reboot the system hangs.  I've tried all of the options in the grub menu and the result is the same.

Right now I've booted using the CD-Rom

1. Is there an easy fix?

2. Can I retireve my data from SATA drive before reinstalling from CD if necessary?

Here's how to mount your Ubuntu root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
Once you mount your root partition, you should be able to open Nautilus, navigate to the directory where you've mounted it and drag & drop files to an external drive.

You might want to post the output of:
```
sudo fdisk -l
```

After you've mounted your root partition, then post the output of your menu.lst & fstab...the link I gave you explains it pretty well, but ask if you have questions.

You might want to run this command from the live cd:
```
blkid
```
compare the UUID's in your menu.lst & fstab with the UUID output of "blkid".

Do you get an error message?  If you don't & you're getting a grub boot menu, highlight your Ubuntu entry, press "e", then in the kernel line remove the "quiet" &  "splash" options(think you have to press "e" again, then maybe enter), then press "b" to boot.  This may show where the system is hanging during boot.

---

### Post by anafshalom on 2007-06-21
I was able to mount my drive and get the important files!  Thanks

Here is sudo fdisk -l

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         981     7879851   83  Linux
/dev/hda2             982        1027      369495    5  Extended
/dev/hda5             982        1027      369463+  82  Linux swap / Solaris


Here is menu.lst

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Here is fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>      		 <dump>  <pass>
proc                       /proc           proc    defaults     		        0       0
/dev/hda1                /                 ext3    defaults,errors=remount-ro 0       1
/dev/hda5            none               swap    sw             		            0       0
/dev/hdb           /media/cdrom0   udf,iso9660 user,noauto               0       0
/dev/fd0          /media/floppy0     auto     rw,user,noauto  	             0       0

Here is sudo blkid
/dev/hda1: LABEL="/" UUID="51f8f02a-6309-43f3-9d99-bec16300a2f4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: TYPE="swap" 

I don't see any UUID's in the other files.  I can select one of the recovery mode boot options which dumps lots of info in the screen.  Is it saved in a log somewhere?

I did look at it a few times, and it always stops in the sameplace, I can't remember what that is, but I will check.

Do you think I should just reinstall from the Live CD now that I have what I need?

---

### Post by confused57 on 2007-06-21
Since you have your data backed up, I would definitely suggest a "clean" install of Dapper...you might want to set up a separate /home partition, so that next time you could install a newer version of Ubuntu and keep your /home unformatted when you install the newer version... upgrades can be problematic.
You could also consider setting up a separate ext3 /media/data partition to store data files on, instead of a separate /home.

---

### Post by anafshalom on 2007-06-21
Thanks!  

I'm going to clean it all up and start again!

---

### Post by confused57 on 2007-06-21
> **anafshalom said:**
> Thanks!  

I'm going to clean it all up and start again!
Glad to help...my suggestions are from personal experience.  When I first installed Breezy 18 months ago, I just used the default install of a root and swap partition...thank goodness the update to Dapper went OK.  Now anytime I install Ubuntu, I set up a separate /home, as well as, a separate data partition...it would depend on how large your hard drive is and how much data you will be saving.  With a separate data partition, your /home partition could probably be smaller than without the data partition.

---

### Post by anafshalom on 2007-06-23
> **confused57 said:**
> Glad to help...my suggestions are from personal experience.  When I first installed Breezy 18 months ago, I just used the default install of a root and swap partition...thank goodness the update to Dapper went OK.  Now anytime I install Ubuntu, I set up a separate /home, as well as, a separate data partition...it would depend on how large your hard drive is and how much data you will be saving.  With a separate data partition, your /home partition could probably be smaller than without the data partition.

2 questions
1. Do I specify the mount point /home when doing partition during installation, or do I just create the partitions and do the migration afterwards?

2. Can I do all of this (for another system) after the system is already up and running?  Make the partitions (on same drive as root) and migrate the folders over?

---

### Post by confused57 on 2007-06-23
> **anafshalom said:**
> 2 questions
1. Do I specify the mount point /home when doing partition during installation, or do I just create the partitions and do the migration afterwards?

2. Can I do all of this (for another system) after the system is already up and running?  Make the partitions (on same drive as root) and migrate the folders over?

1.)  Yes, just select the mountpoint "/home" for the partition when you install Ubuntu, it would be used for /home just as if it were on the same partition as root...format as ext3.

2.) You can create a separate /home if you didn't when you installed Ubuntu:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

It's much easier to set up a separate /home when you install.

---

