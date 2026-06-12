---
title: "HELP! 13.10 upgrade problem"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by woodsyboredom on 2013-10-19
I was upgrading to 13.10 from 13.04 when my laptop (DELL Inspiron) shut down. Now when I boot I get this message:

Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored. 

then I get a prompt. I don't know what to do. any ideas?

---

### Post by heir4c on 2013-10-19
See this link with the same error:
[http://ubuntuforums.org/showthread.php?t=2181751](http://ubuntuforums.org/showthread.php?t=2181751)

---

### Post by woodsyboredom on 2013-10-19
Yes it is the same error message. I entered fsck -f and the files were checked and cleared. I rebooted and I get the same error message. I rebooted in recovery mode and got the same message. I can't remove the hard drive because I have a laptop and don't know how. any other ideas?

---

### Post by oldfred on 2013-10-19
From liveCD or flash drive, you can try full fsck.

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by woodsyboredom on 2013-10-20
I seem to be unable to do anything. I think I need to somehow force a filesystem mount but I don't know how.
I also tried to instsall from a usb flash drive and set up a partition to avoid losing my stored data, so now I have a version of 13.04 and 13.10 on my laptop. 
I am however unable to open the 13.10. The 13.04 will open but it won't or can't access any of the data. I wanted to upgrade my 13.04 UbuntuStudio to 13.10 UbuntuStudio when this error happened.
I have UbuntuStudio 13.10 on a usb flash drive and can run it live on my laptop. When I do I can partially access data in both partitions. When I tried to install from that flash drive, it won't simply upgrade the existing version of 13.10, but wants to erase everything or set up a second version of 13.10 in a new partition.

I still get this error message whenever I try to boot the 13.10 version that is claims to be currently installed. 

Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored. 

I have run all of the the checks that have been suggested and although they seem to work fine. I can't seem to get the filesystem to mount with the version of 13.10 that is installed nor upgrade that version. I do NOT want to loose the 390 or so GB's of data I have on the hard drive. Anyone have any new ideas?

---

### Post by oldfred on 2013-10-20
I think if system sees any issue it will not mount partition. And install will not see a partition that you cannot mount so it only offers to overwrite entire system.

some more advanced possibilities:
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
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

