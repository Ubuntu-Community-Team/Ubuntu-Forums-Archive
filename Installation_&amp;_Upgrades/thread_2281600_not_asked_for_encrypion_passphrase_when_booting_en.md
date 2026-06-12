---
title: "not asked for encrypion passphrase when booting encrypted drive after upgrade to 15.0"
date: 2015-06-08
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2015-06-08
I've had '/' and '/home' on two separate encrypted drives and was always prompted for both passphrases during boot.

After upgrading to 15.04, I'm only prompted for the '/home' drive.

Following is the the fstab file, the /dev/mapper folder and the result from df

Thanks

Leo



llist@LeosGameLaptop:/var/log$ more /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/sda2_crypt /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=10585694-d533-4792-800a-f5121a20b432 /boot           ext4    defaults        0       2
/dev/mapper/sda4_crypt /home           ext4    defaults        0       2
/dev/mapper/sda5_crypt none            swap    sw              0       0
llist@LeosGameLaptop:/var/log$ ls -lsa /dev/mapper
total 0
0 drwxr-xr-x  2 root root     120 Jun  8 13:24 .
0 drwxr-xr-x 20 root root    5240 Jun  8 13:24 ..
0 crw-------  1 root root 10, 236 Jun  8 13:24 control
0 lrwxrwxrwx  1 root root       7 Jun  8 13:24 sda2_crypt -> ../dm-0
0 lrwxrwxrwx  1 root root       7 Jun  8 13:24 sda4_crypt -> ../dm-2
0 lrwxrwxrwx  1 root root       7 Jun  8 13:24 sda5_crypt -> ../dm-1
llist@LeosGameLaptop:/var/log$ df -h
Filesystem              Size  Used Avail Use% Mounted on
udev                    7.8G     0  7.8G   0% /dev
tmpfs                   1.6G   11M  1.6G   1% /run
/dev/dm-0               138G   12G  120G   9% /
tmpfs                   7.8G  156K  7.8G   1% /dev/shm
tmpfs                   5.0M  4.0K  5.0M   1% /run/lock
tmpfs                   7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1               1.9G  113M  1.6G   7% /boot
/dev/mapper/sda4_crypt  763G  535G  190G  74% /home
tmpfs                   1.6G   52K  1.6G   1% /run/user/1000
/dev/sdb3                18G  676M   17G   4% /media/llist/a27ca082-db83-46be-add6-b58eea9d6661
/dev/sdb2               518G  455G   38G  93% /media/llist/42f15844-5afc-41d4-ae97-3d918a666a5f
/dev/sdb1               1.3T  1.1T  238G  83% /media/llist/41481C8B5686EF95
encfs                   763G  535G  190G  74% /home/llist/pers1
encfs                   763G  535G  190G  74% /home/llist/pers2

---

### Post by lister171254 on 2015-06-09
more info. I did the following and the result seems to indicate that "/" "/home" and swap are encrypted.

Question is why is df not showing "/" and swap as "/dev/mapper/sda...."

llist@LeosGameLaptop:~$ sudo blkid 
/dev/mapper/sda2_crypt: UUID="17e3ce8c-ceb9-49bd-9387-15925fd4d512" TYPE="ext4"
/dev/sda1: UUID="10585694-d533-4792-800a-f5121a20b432" TYPE="ext4" PARTUUID="70669437-01"
/dev/sda2: UUID="0043e354-ccdf-4e1e-a619-1ff210375cbd" TYPE="crypto_LUKS" PARTUUID="70669437-02"
/dev/sda4: UUID="884ee544-b6d6-49e5-a99d-bbf4e86c4b3b" TYPE="crypto_LUKS" PARTUUID="70669437-04"
/dev/sda5: PARTUUID="70669437-05"
/dev/sdb1: UUID="41481C8B5686EF95" TYPE="ntfs" PARTUUID="3ac308c7-01"
/dev/sdb2: UUID="42f15844-5afc-41d4-ae97-3d918a666a5f" TYPE="ext4" PARTUUID="3ac308c7-02"
/dev/sdb3: UUID="a27ca082-db83-46be-add6-b58eea9d6661" TYPE="ext4" PARTUUID="3ac308c7-03"
/dev/sdc1: UUID="72DCBA59DCBA1777" TYPE="ntfs" PARTUUID="1766a869-01"
/dev/mapper/sda5_crypt: UUID="8a5ac623-5e13-4a3b-8fe7-5e0b6d8c41cf" TYPE="swap"
/dev/mapper/sda4_crypt: UUID="8e3687f1-2ba7-4a53-bb45-589b4b06e39d" TYPE="ext4"
/dev/sdd: LABEL="SANSA CLIPZ" UUID="6436-B2EF" TYPE="vfat"

---

### Post by lister171254 on 2015-07-05
After further checks I found that only sda2 is encrypted at boot

---

### Post by lisati on 2015-07-07
Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

Duplicate of [http://ubuntuforums.org/showthread.php?t=2285587](http://ubuntuforums.org/showthread.php?t=2285587) closed.

If you think a thread should be moved to a different section of the forum, you can always ask the forum staff to take a look by using the "Report Post" function.

---

