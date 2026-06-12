---
title: "[SOLVED] GRUB error 18"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by danjdel on 2007-12-25
I am attempting to install ubuntu 7.10 to dual-boot with XP on my averatec 3280 laptop. After running into problems getting the live CD to work, I looked at this forum: 
[http://ubuntuforums.org/showthread.php?p=3992223](http://ubuntuforums.org/showthread.php?p=3992223)

and discovered that I had to use the alternate. For partitioning, I chose the option of resizing the XP partition and using the free space for ubuntu. I went with the default option for GRUB of installing it on the master boot record. When I booted, I got the following output:

GRUB loading stage1.5.


GRUB loading, please wait . . . 
Error 18



From research online I found that I need a boot partition to fix the problem that the disk is too big to boot to the ubuntu partition. The problem is that I don't know how to do that, particularly with no OS. I tried using the "rescue broken system" option on the alternate, but was unsuccessful in finding what I need. I can get to the "execute shell in /dev/hda2" and "execute shell in installer environment" options, so if I knew what (if any) commands typed there would properly make the boot partition, I could do that.

---

### Post by muskratmx on 2007-12-26
The problem is your cmos is unable to read that far back on the disk.

There is several choices,

One; Use a third party boot loader. (Which I wouldn't do, just because I love grub)
Two; put linux on a second drive, then swap positions and place the windows drive in slave   postion, and grub can boot windows from there.
Three; (Requires windows to be reinstaled) I've never done this but it's posible to place windows on partion 2. make a small partion for /boot the one for windows both within your cmos limits. then your root partition of linux.

---

### Post by danjdel on 2007-12-26
Thanks.
Hmm, I don't want to reinstall Windows, though I guess I could if absolutely necessary. I'm using a laptop so 2nd HDDs aren't really an option. 

Does anyone know have advice on how to fix this while keeping grub or a good 3rd-party boot loader that would easily fix my issues?

---

### Post by Pumalite on 2007-12-26
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by psusi on 2007-12-26
You just need to create a 100-150 mb partition near the start of the disk ( under the 8 gb mark ) and mount it as /boot when you are at the partitioning stage of the Ubuntu installation.

If you already have a windows partition that starts at 0 and goes beyond 8 gb, then you will have to reinstall windows, since I I don't think gparted will let you move the start of the partition.

---

### Post by danjdel on 2007-12-26
Ok, I've decided that I'm going to make the boot partition and reinstall XP and ubuntu. Anyone have a good guide on making the boot partition?

---

### Post by psusi on 2007-12-27
Boot the Ubuntu livecd and start up gparted.  Blow away all partitions and create one that is ext3 and about 100-150 MB.  Then reboot and install windows, leaving enough free space to later install Ubuntu.  When installing Ubuntu, define that first partition as /boot, and use the free space for /.

---

### Post by Pumalite on 2007-12-27
Better use Gparted Live CD (is not a good idea to partition mounted drives):
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and do your job.

---

### Post by psusi on 2007-12-27
Gparted comes on the Ubuntu LiveCD, so there's no need to download and burn another.

---

### Post by Pumalite on 2007-12-27
Wrong. The Gparted in the Live CD works with mounted drives and is not the one I suggested.
Besides that is a newer version, more flexible and more powerful.

---

### Post by psusi on 2007-12-27
> **Pumalite said:**
> Wrong. The Gparted in the Live CD works with mounted drives and is not the one I suggested.
Besides that is a newer version, more flexible and more powerful.

No it doesn't; gparted can't manipulate mounted drives because the kernel won't allow it.  The gparted livecd does contain a newer version, but that shouldn't make any difference.

---

### Post by danjdel on 2007-12-27
Ok, thanks everyone. I got it all working.

---

