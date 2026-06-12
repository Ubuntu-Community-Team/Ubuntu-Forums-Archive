---
title: "how to get ubuntu to recognize recovered partition table?"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by rizos on 2013-06-30
i had a dual partition (windows 7-ubuntu & 12.04) was trying to make a fresh install and by mistake i did got to install  ubuntu deleting all the disk, fortunately i was able to rescue the  partition table via testdisk, i can  see my files via sudo ecryptfs-recover-private. but there is no way i  can copy them into a usb so i can reinstall and get my pc working again  (says i dont have the permission to copy such files). i had a partition  for windows 7, a partition just for ubuntu OS, another for swap and last  one for all my files (music. photos etc etc). i tried to fix the MBR  for windows via Boot-repair and got mess some how as i cant bring the  windows partition back.i know home folder is there and all my files. how can i  bring back the system as it was, so later on i can re-install ubuntu on  the partition for the OS. 

here is the full out put of partition table via boot repair. [http://paste.ubuntu.com/5815124/](http://paste.ubuntu.com/5815124/)

i made a new thread as my first question was kind of solved ([http://ubuntuforums.org/showthread.php?t=2158610](http://ubuntuforums.org/showthread.php?t=2158610)) but this is entirely another issue, so i come with a new question.


thanx.

---

### Post by Mark Phelps on 2013-07-01
You actually had TWO partitions for Win7: a small boot partition and a larger OS partition.  You appear to have forced GRUB into BOTH partitions -- a bad idea.  Also, the script shows no record of the Windows boot loader files or folders.  So basically, you have no way to boot Win7.

The general way to fix that from Linux is to run Boot-Repair.

While Boot-Repair often works, ,my own preference is to fix Windows boot problems with Windows utilities, not Linux utilities.

While Win7 was working, you COULD have made a boot repair disk quickly and for FREE -- but since you failed to do that, you need to go to the site in the link and purchase a Windows Repair CD ISO:  [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Burn that ISO to CD, and run it three times -- that's right, three times.  That will rewrite the Win7 boot loader files.

But BEFORE you do that, boot into Ubuntu and see if you can remove the GRUB files and folders from both sda1 and sda2.

---

### Post by rizos on 2013-07-01
i fix the windows issue, now i can log into windows no problem, windows also reads that i have 4 partitions (1 windows, 2 ubuntu OS, 3 swap, 4 ubuntu files). now i cant boot into ubuntu, gparted via livecd wont read the partition as windows does  (only reads one huge empty partition)  fstab reads overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

but blkid gives this.
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="6A7ACF807ACF4811" TYPE="ntfs" 
/dev/sda2: UUID="38A6D1F9A6D1B798" TYPE="ntfs" 
/dev/sda3: UUID="69ccfbd9-c092-4c2e-a708-3e10fa5dc742" TYPE="ext4" 
/dev/sda5: UUID="76ef0b21-c083-4734-83c7-db7d0fcc7b67" TYPE="ext4" 
/dev/sdb1: UUID="0D9E-46B7" TYPE="vfat" 

is there a way to have gparted read the partition table as the blkid, so that way i can reinstall ubuntu fresh on the partiton for the OS with out damaging my files?.

---

