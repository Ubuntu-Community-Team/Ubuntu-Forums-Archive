---
title: "Can't boot new installation of 14.04"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by damien7 on 2014-05-21
Hi, 

Using Wubi I just installed Ubuntu on a Samsung netbook (NC10) alongside Win XP. The installation seemed to go fine, but when I reboot and select Ubuntu I get a message 'Serious errors were found while checking the disk for /.' 

If I hit 'S' for skip, I get another message 'The disk drive for /temp is not ready yet or not set'. 

The other option for manual fix takes me to a logon prompt and then a DOS-like Ubuntu prompt.

Not sure where to go from here so grateful for any pointers. I've run chkdsk/r but everything seems fine on the HD.

Cheers,
Damien

---

### Post by oldfred on 2014-05-21
Wubi runs inside the Windows NTFS partition and uses the Windows boot loader for initial startup.
Note that 12.04 is the last supported version of wubi. All new computers now use gpt partitioning and UEFI booting, so wubi does not work with new computers. It still is available but you are on your own in trying to use it. And that is the opposite of what wubi is/was all about.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You may need to run fsck which is like chkdsk but for ext2, ext3 & ext4 formatted partitions. 
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: > Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


---

### Post by damien7 on 2014-05-21
OK, thanks for that. I tried a new installation with LiLi and that worked fine so problem solved.

---

