---
title: "Fat32 partition not accessible from win2k after writing to it in Ubuntu"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by Ba|der on 2006-10-13
I have an iBuddie4 laptop with a 40Gb HDD. It have dualboot Win2k Pro[norwegian] with Ubuntu 6.06 Drake Dapper. Ubuntu have installed grub in the MBR.

What i want: A shared 2Gb FAT32 partition for sharing files between Win2k and Ubuntu.

Problem:
After installing Ubuntu without writing anything to the FAT32 partition it works fine in Win2k. After writing to it in Ubuntu the partition is not listed in explorer in Windows, and in Adm-tools- Disc management it is no longer listed as a FAT32 partition (no info on type) and trying to add a drive letter to it results in error partition is not set active, you need to reboot. Reboot=NoGo. I also tried setting it to active with windws disc management but it just crashed. (I think only the boot partiton should be have active flag set.)

TS:
I have also tried to get it work with Ubuntu 5.10=NoGo.
Removed all partitions except NTFS(with win2k) and installed Ubuntu 5.10 and later removed again and tried same with Ubuntu 6.06 and added partitions during Ubuntu install. Works in Win2k untill I write to it in Ubuntu. Also tried a Gentoo-resque CD with QT-parted and removed FAT32 part. and readded it. Worked first time in win2k, then stopped working after writing to it in Ubuntu. I have also tried changing the default config in /etc/fstab but no luck so far, but I think the problem might be here(?) I have tried using a primary fat32 partition and an extended partition on a logical partition=NoGo.

I also read on <URL: http://www.partitionsupport.com/partitionnotes.htm> that win2k does not respect hidden partitons as WinXP does, maybe that has something to do with it?

I have read a lot of guides on mounting extra partitions with Ubuntu, but none of them seems to mention this problem or how to solve it. Any help is appriciated.

---

### Post by galileon on 2006-10-13
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm) allows you to access ubuntu partition from windoze,

[http://sourceforge.net/mailarchive/forum.php?forum_id=2697&thread_id=23836054](http://sourceforge.net/mailarchive/forum.php?forum_id=2697&thread_id=23836054)
allows you to access windoze partitions from ubuntu...

you wont need the shared partition then..

---

### Post by dannyboy79 on 2006-10-13
> **galileon said:**
> [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm) allows you to access ubuntu partition from windoze,

[http://sourceforge.net/mailarchive/forum.php?forum_id=2697&thread_id=23836054](http://sourceforge.net/mailarchive/forum.php?forum_id=2697&thread_id=23836054)
allows you to access windoze partitions from ubuntu...

you wont need the shared partition then..

i was about to post that but after reading his post over again, i see that his partition isn't formatted ext3, he is saying that it's formatted as fat32 but then when he writes something to it FROM ubuntu, it makes the entire partition unreadable in Win 2K. Sounds like you need to get rid of Win2k!  HA HA. No, just kidding. Something is terribly wrong here because I have a fat32 partition that was formatted using windows 98 (I think) that I have mounted all the time in ubuntu, i write to it all the time, and then I can retrieve from it using my xbox (media center, i stream music and movies from my fat32 partition to my xbox) and I also can save to it and see it from winxp. I wish I could help you. Why don't you post your fstab. It also sounds weird that your saying you can't even change your fstab, something is really wrong with this! are using sudo?

---

### Post by Ba|der on 2006-10-13
> **dannyboy79 said:**
> [...] Why don't you post your fstab.[...]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
**/dev/hda2       /home/balder/fat32 vfat    defaults,utf8,umask=007,gid=46 0       1**
/dev/hda1       /windows/c      ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

This is my latest fstab, as I wrote earlier (and I have now edit first post to clearify misunderstanding) I have tried changing the options parameter with tips from differnt guides. It takes time to try differnt options due to I have to remove the fat32 partition and add it again each time.

I will have a look into the earlier post about getting ext3 support for Windows, but I am afraid that is not a stable solution. Having Ubuntu to write to my NTFS-partition is a to big risk-factor, that's why I wanted to have a separate FAT32 partition that both Operating Systems could use, and as a well tested solution.

---

### Post by Freddy on 2006-10-13
Samt thing happend to me, windows doesn't see my fat32 partition. Is your fat32 partition over 127gb, cause i think it's a lba problem.

---

### Post by dannyboy79 on 2006-10-13
> **Freddy said:**
> Samt thing happend to me, windows doesn't see my fat32 partition. Is your fat32 partition over 127gb, cause i think it's a lba problem.

mine is 200gb. are you guys talking about ata or sata interface? your fstab looks similar to mine. check mine out.
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0

---

### Post by Ba|der on 2006-10-14
> **Freddy said:**
> Samt thing happend to me, windows doesn't see my fat32 partition. Is your fat32 partition over 127gb, cause i think it's a lba problem.

As I wrote in my first post, the HDD is on "40GB", so I sat the FAT32 partition is to 2048Mbytes. 

Anyway, I'm now reinstalling Win2k Pro [norwegian], and it seems to work now (I hope it will continue to do so). I will install the rest of the updates for both ubuntu and Win2k and cross my finger it will still work. My win2k installation was a bit old nyway, but it's just painful to reinstall. I've at least lost all information from programs storing it in the Windows registry. On the old installation I had installed so much software during it's use, like filesystem drivers for UDF-filesystems etc so something was probably incompatible with the standard way of handling things.

---

