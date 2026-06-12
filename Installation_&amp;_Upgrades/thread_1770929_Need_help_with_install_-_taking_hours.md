---
title: "Need help with install - taking hours"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by Jphoward78 on 2011-05-29
Hi there,

I am trying to install Ubuntu for the first time, so please excuse me if this sounds naive.

I have Windows7 on an SSD and a second HDD with the same NTFS.  I have selected the HDD for installation with Ubuntu, and asked to create a 250MB partition on that second drive.

I am installing the latest desktop version of Ubuntu, 32-bit.  I have been waiting several hours for the installation to occur, but it has allowed me to open a web browser in the background, so obviously the system is still operating (I am typing this up within that web browser).  The line in the install window says:

>> Creating ext4 file system for / in partition #5 of SCSI2 (0,0,0) (sdb) ...

The last statement in the console says:

>> ubuntu AptDaemon: INFO: Initializing deamon
>> ubuntu AptDaemon: INFO: Quitting due to inactivity
>> ubuntu AptDaemon: INFO: Shutdown was requested
>> ubuntu CRON[10804]: (root) CMD (   cd / && run-parts  - - report tc/cron.hourly)

My common sense tells me that someone has gone wrong, and I don't know if I should restart my system if it's in progress of doing something with my drives.

Previously in the log, it has the following error:

>> Error: Count not find the path /mnt/migrationassestant/WINDOWS/system32/config/software
>> Error: Count not find the path /mnt/migrationassestant/WINNT/system32/config/software
>> Fatal: Could not find the SOFTWARE registry hive at /mnt/migrationassistant/WINNT/system32/config/software
>> ubuntu ntfs-3g[9553]: Unmounting /dev/sdal (System Reserved)
>> ubuntu ubiquity[3104]: migration-assistant: filtering out Windows 7 Loader) (/dev/sdal) as it has no users
>> ubuntu ubiquity[3104]: debconffilter_done: ubi-migrationassistant (Current: ubi-migrationassistant)
>> ubuntu ubiquity[3104]: Step_before = stepUserInfo
>> ubuntu CRON[9815]: (root) CMD (   cd / && run-parts  - - report tc/cron.hourly)


Can someone please give me some advice, or help to show me how to debug this further?  Or should I just wait longer?

Thanks in advance.

Jeff

---

### Post by Phil465 on 2011-08-03
I am have the same problem.

---

### Post by steve11911 on 2011-08-05
Some details would be helpful.Hard drives? System hardware? Ubuntu version/install media info...etc.
This page is a good place to start:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
One of the wise guru's on this site has advised running Ubuntu from the live cd for awhile to assure compatibility...

---

