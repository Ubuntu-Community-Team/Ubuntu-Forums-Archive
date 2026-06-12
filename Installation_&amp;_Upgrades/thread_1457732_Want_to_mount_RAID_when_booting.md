---
title: "Want to mount RAID when booting"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by misterfixit on 2010-04-19
After update/upgrade; previously existing RAID no longer auto-mounts.

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1125

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5100       30393   203174055   83  Linux
/dev/sda2               1        5099    40954880+   5  Extended
/dev/sda5               1        4885    39229440   83  Linux
/dev/sda6            4885        5099     1724416   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f1e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       91201   732572001   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006f1e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001   83  Linux
root@dave-desktop:/home/dave# mdadm
Usage: mdadm --help
  for help
root@dave-desktop:/home/dave# mdadm --assemble /dev/md0 /dev/sdb1 /dev/sbc1
mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted


Anyone wish to help me?

---

### Post by misterfixit on 2010-04-19
Bump? ! ?

Anyone at all help me get this RAID mounted at boot time?????  Please?

---

### Post by lyall on 2010-04-19
have you checked the Community Documentation for InstallationSoftwareRAID [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

and FakeRaidHowto [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

hope this helps you, it is a place to start
also check Community Documentation [https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")
 and search for raid
for additional info

good luck and and have learning

---

### Post by misterfixit on 2010-04-20
> **lyall said:**
> have you checked the Community Documentation for InstallationSoftwareRAID [https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

and FakeRaidHowto [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

hope this helps you, it is a place to start
also check Community Documentation [https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")
 and search for raid
for additional info

good luck and and have learning

OK, here is what I have gotten this far.

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_jfgfbeha" already active
RAID set "nvidia_jfgfbeha1" already active

ubuntu@ubuntu:~$ sudo ls -l /dev/mapper total 0
crw-rw---- 1 root root  10, 59 2010-04-20 11:50 control
brw-rw---- 1 root root 252,  0 2010-04-20 11:50 nvidia_jfgfbeha
brw-rw---- 1 root root 252,  2 2010-04-20 11:50 nvidia_jfgfbeha1
ubuntu@ubuntu:~$ 

I see that both of my 1TB devices are there and active.  My next question is HOW to automatically mount them to /mnt/RAID

Shall I add to fstab something like /dev/mapper  /mnt/RAID  ... etc  ???

I do NOT want to take chances with this RAID array .. it is contains valuable information which is backed up, but will be difficult to separate back to the bare metal install.

Thank you for the helpful pointer towards my success!

Dave

---

### Post by misterfixit on 2010-04-21
> **misterfixit said:**
> OK, here is what I have gotten this far.

ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_jfgfbeha" already active
RAID set "nvidia_jfgfbeha1" already active

ubuntu@ubuntu:~$ sudo ls -l /dev/mapper total 0
crw-rw---- 1 root root  10, 59 2010-04-20 11:50 control
brw-rw---- 1 root root 252,  0 2010-04-20 11:50 nvidia_jfgfbeha
brw-rw---- 1 root root 252,  2 2010-04-20 11:50 nvidia_jfgfbeha1
ubuntu@ubuntu:~$ 

I see that both of my 1TB devices are there and active.  My next question is HOW to automatically mount them to /mnt/RAID

Shall I add to fstab something like /dev/mapper  /mnt/RAID  ... etc  ???

I do NOT want to take chances with this RAID array .. it is contains valuable information which is backed up, but will be difficult to separate back to the bare metal install.

Thank you for the helpful pointer towards my success!

Dave



Once again, Bump .. I am patiently waiting for someone to assist me in this matter.

Regards,

Dave

---

### Post by Ichimonji10 on 2010-06-22
I've found the single most helpful page on raid to be this one, here: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) However, I usually use mdadm to manage RAID sets; looks like you're using dmraid instead.

If you want to automatically mount a mirror on startup, you need three things: a working mirror (such as /dev/md0), a place to mount the mirror, and an entry in the fstab. It sounds to me like you are looking for the third.

I'd simply create an entry in the fstab that looks like this:
/dev/md0    /media/mirror0    ext4    auto,nouser,rw,exec    0    0

Where /dev/md0 is the logical partition (RAID set), /media/mirror0 is where the mirror is mounted, and ext4 is the filesystem on the disks.

BEFORE you go and try fooling around with the fstab, try mounting the array manually. For example, do this:
cd /media
sudo mkdir mirror0
sudo mount /dev/md0 /media/mirror0
If it fails, tail /var/log/messages for hints as to what went wrong.

Also, what's the output of cat /proc/partitions and dmraid -rD

---

