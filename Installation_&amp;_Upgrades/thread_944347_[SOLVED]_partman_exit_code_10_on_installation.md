---
title: "[SOLVED] partman exit code 10 on installation"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by sartorius on 2008-10-11
Hey, folks.  I looked to see if this question's been asked before, but if so I can't find it.  

I'm completely new to Linux and I installed Ubuntu in a dual-boot menu (with Windows XP as the other option).  It's not running from a cd.  When I let the computer boot, it eventually goes into what seems to be a 7-part process of finalizing the installation.  Every time it does this, it gets to a part right after setting the clock where it says 'Starting up the partitioner'.  After 30 seconds it says Partman failed with exit code 10, and that I should check /var/log/syslog for details.  The options are:
- quit
- continue anyway
- try again

If I retry, nothing else happens for up to 10 minutes except for a flashing light on my external HDD.  I eventually give up and hit cancel to skip the rest of installation.  Then I guess it's a generic Ubuntu session.  At the top of the screen it says 'Live session user'.

Otherwise, if I'm adventurous I select 'continue anyway' where the next window ('Who are you?' / step 5 of 7) ends with an error: Summary failed with exit code 141.  Then it kicks me back to:
'Prepare disk space.  How do you want to partition the disk?' / step 4 of 7
After another 10 minutes I hit 'cancel', then 'quit', and end up as 'Live session user'.

What can I do to finish the installation?

If it matters, here's some info about my computer:
emachines t3256 (as a side note, I have no idea how to access the bios)
160 GB internal HDD
1 TB external HDD

Below I pasted what seems to be the relevant bit of /var/log/syslog.  I can paste the entire file here, but I don't yet know if that comes across as making an excessively large post.  But if you want it, I've got it ready...






Oct 11 12:55:32 ubuntu ubiquity[8888]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Oct 11 12:55:32 ubuntu ubiquity[8888]: Step_before = stepLocation
Oct 11 12:55:46 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 11 12:55:46 ubuntu ntfsresize: Device name        : /dev/sda1
Oct 11 12:55:46 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 11 12:55:46 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 11 12:55:46 ubuntu ntfsresize: Current volume size: 160039240192 bytes (160040 MB)
Oct 11 12:55:46 ubuntu ntfsresize: Current device size: 160039240704 bytes (160040 MB)
Oct 11 12:55:46 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 11 12:55:46 ubuntu ntfsresize: Accounting clusters ...
Oct 11 12:55:46 ubuntu ntfsresize: Space in use       : 47244 MB (29.5%)
Oct 11 12:55:46 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 11 12:55:46 ubuntu ntfsresize: You might resize at 47243264000 bytes or 47244 MB (freeing 112796 MB).
Oct 11 12:55:46 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 11 12:55:49 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 11 12:55:49 ubuntu ntfsresize: Device name        : /dev/sdb1
Oct 11 12:55:49 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 11 12:55:49 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 11 12:55:49 ubuntu ntfsresize: Current volume size: 1000202240512 bytes (1000203 MB)
Oct 11 12:55:49 ubuntu ntfsresize: Current device size: 1000202241024 bytes (1000203 MB)
Oct 11 12:55:49 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 11 12:55:49 ubuntu ntfsresize: Accounting clusters ...
Oct 11 12:55:49 ubuntu ntfsresize: Space in use       : 82528 MB (8.3%)
Oct 11 12:55:49 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 11 12:55:49 ubuntu ntfsresize: You might resize at 82527121408 bytes or 82528 MB (freeing 917675 MB).
Oct 11 12:55:49 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 11 12:55:52 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 11 12:55:52 ubuntu ntfsresize: Device name        : /dev/sdb1
Oct 11 12:55:52 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 11 12:55:52 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 11 12:55:52 ubuntu ntfsresize: Current volume size: 1000202240512 bytes (1000203 MB)
Oct 11 12:55:52 ubuntu ntfsresize: Current device size: 1000202241024 bytes (1000203 MB)
Oct 11 12:55:52 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 11 12:55:52 ubuntu ntfsresize: Accounting clusters ...
Oct 11 12:55:52 ubuntu ntfsresize: Space in use       : 82528 MB (8.3%)
Oct 11 12:55:52 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 11 12:55:52 ubuntu ntfsresize: You might resize at 82527121408 bytes or 82528 MB (freeing 917675 MB).
Oct 11 12:55:52 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 11 12:55:54 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 11 12:55:54 ubuntu ntfsresize: Device name        : /dev/sda1
Oct 11 12:55:54 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 11 12:55:54 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 11 12:55:54 ubuntu ntfsresize: Current volume size: 160039240192 bytes (160040 MB)
Oct 11 12:55:54 ubuntu ntfsresize: Current device size: 160039240704 bytes (160040 MB)
Oct 11 12:55:54 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 11 12:55:54 ubuntu ntfsresize: Accounting clusters ...
Oct 11 12:55:54 ubuntu ntfsresize: Space in use       : 47244 MB (29.5%)
Oct 11 12:55:54 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 11 12:55:54 ubuntu ntfsresize: You might resize at 47243264000 bytes or 47244 MB (freeing 112796 MB).
Oct 11 12:55:54 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 11 12:55:57 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 11 12:55:57 ubuntu ntfsresize: Device name        : /dev/sdb1
Oct 11 12:55:57 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 11 12:55:57 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 11 12:55:57 ubuntu ntfsresize: Current volume size: 1000202240512 bytes (1000203 MB)
Oct 11 12:55:57 ubuntu ntfsresize: Current device size: 1000202241024 bytes (1000203 MB)
Oct 11 12:55:57 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 11 12:55:57 ubuntu ntfsresize: Accounting clusters ...
Oct 11 12:55:57 ubuntu ntfsresize: Space in use       : 82528 MB (8.3%)
Oct 11 12:55:57 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 11 12:55:57 ubuntu ntfsresize: You might resize at 82527121408 bytes or 82528 MB (freeing 917675 MB).
Oct 11 12:55:57 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 11 12:55:57 ubuntu ubiquity[8888]: debconffilter_done: Partman (current: Partman)
Oct 11 12:55:57 ubuntu ubiquity[8888]: dbfilter_handle_status: ('Partman', 10)
Oct 11 12:56:01 ubuntu ubiquity[8888]: dbfilter_handle_status: response -7
Oct 11 12:56:01 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Oct 11 12:56:01 ubuntu ubiquity[8888]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Oct 11 12:56:01 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Oct 11 12:56:01 ubuntu ubiquity[8888]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Oct 11 12:56:03 ubuntu /usr/sbin/cron[10049]: (CRON) INFO (pidfile fd = 3)
Oct 11 12:56:03 ubuntu /usr/sbin/cron[10050]: (CRON) STARTUP (fork ok)
Oct 11 12:56:03 ubuntu /usr/sbin/cron[10050]: (CRON) INFO (Running @reboot jobs)
Oct 11 12:56:07 ubuntu pulseaudio[10306]: pid.c: Stale PID file, overwriting.
Oct 11 12:56:07 ubuntu pulseaudio[10306]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 11 12:56:09 ubuntu hcid[8676]: Default passkey agent (:1.30, /org/bluez/passkey) registered
Oct 11 12:56:09 ubuntu hcid[8676]: Default authorization agent (:1.30, /org/bluez/auth) registered
Oct 11 12:56:15 ubuntu NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 11 12:56:15 ubuntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 11 12:56:19 ubuntu ntfs-3g[10440]: Version 1.2216 external FUSE 27 
Oct 11 12:56:19 ubuntu ntfs-3g[10440]: Mounted /dev/sdb1 (Read-Write, label "My Book", NTFS 3.1) 
Oct 11 12:56:19 ubuntu ntfs-3g[10440]: Cmdline options: rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8 
Oct 11 12:56:19 ubuntu ntfs-3g[10440]: Mount options: rw,nosuid,nodev,uhelper=hal,silent,allow_other,nonempty,relatime,noatime,fsname=/dev/sdb1,blkdev,blksize=4096 
Oct 11 12:56:19 ubuntu hald: mounted /dev/sdb1 on behalf of uid 999

---

### Post by sartorius on 2008-10-14
FYI, I learned the difference between copying the .iso file to a cd and burning a cd image.  At least that's what seems to have fixed the problem.

---

### Post by ekawahyu on 2009-04-21
How did you solve your problem, I got the same exit code 10 during installation on Toshiba Netbook NB100-11R. But I got no problem using the Ubuntu recovery CD.

---

