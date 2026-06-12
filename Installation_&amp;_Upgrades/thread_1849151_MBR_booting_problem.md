---
title: "MBR booting problem"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by rovertace on 2011-09-23
I have looked everywhere on this forum, but could not find the answer, 
Problem is that after adding another HD and installing Ubuntu 10.04 on the new drive, now unable to mount my original drive,

sda1 has 10.04 and works ok
sdb1 has Windows XP and works ok,
but sdc1 has this error when I try to mount it.

Unable to mount Trevor11

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Below is a copy of the boot script.

Hope someone can help. thanks in advance

                  Boot Info Script 0.60    from 17 May 2011

---

### Post by oldfred on 2011-09-23
Boot script just shows same error in trying to mount your sdc1 partition.

Have you tried a filecheck?

Since it is sdc, you probably can just do it from you install.

#From liveCD so everything is unmounted,swap off if necessary, change sdc1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdc1
#if errors:
sudo e2fsck -f -y -v /dev/sdc1

---

### Post by rovertace on 2011-09-24
Thanks oldfred,
I tried your suggestion, but this is what I got?
 

tom@Toms:~$ sudo e2fsck -C0 -p -f -v /dev/sdc1
[sudo] password for tom: 

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc1
Could this be a zero-length partition?

tom@Toms:~$ sudo e2fsck -f -y -v /dev/sdc1
e2fsck 1.41.11 (14-Mar-2010)

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdc1
Could this be a zero-length partition?
tom@Toms:~$ 

Does that mean there is nothing on that  partition?
I have(had) data on it for sure, anyway to retrieve it?

Thanks

---

### Post by oldfred on 2011-09-24
Partition table shows partition exists. Several other things to try that I have saved in notes. Others may have better/more specific suggestion based on your error.

What does testdisk show? Testdisk is in repository, Download from synaptic. you may have to enable the "universe" repository to download testdisk

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by rovertace on 2011-09-24
Thanks oldfred,

the info found on[ http://linuxexpresso.wordpress.com/2...ock-in-ubuntu/]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")
Part of testdisk which is in the repositories or most recovery CDs.

did the trick.

great job.

---

### Post by oldfred on 2011-09-24
Glad it worked.:)

---

