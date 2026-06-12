---
title: "Alternate 64bit iso install Raid failure"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by dphurst on 2010-08-27
UPDATE: decided to reinstall and run the partitioner to get rid of the raid.  Not worth dealing with this since seems to be lower level as /dev/mapper was not listing any devices.  Error 15 at grub points to legacy grub.  So avoiding the problem by getting rid of raid for now.  So ignore this post.  Found a nice grub2 explanation on the wiki but didn't help this situation since probably isn't a grub problem.  Probably is a installer failure to map devices properly when it only used what was already available and didn't create them during the install.  I don't know, just guessing.





Had OpenSuSE 10.3 64bit installed with software raid mirrored swap, boot, root.  Used the alternate 64bit Ubuntu iso for installation.  Since partitioning was already correctly setup and the raid devices /dev/md0,1,2 were recognized by the installer, I chose to format the partitions with ext3 and accept the configuration:
/dev/md0 = swap = /dev/sda1, /dev/sdb1 = 2Gb
/dev/md1 = boot = /dev/sda2, /dev/sdb2 = 256Mb
/dev/md2 = root = /dev/sda3, /dev/sda3 = 20Gb

**Installation process failed at the point of installing grub.**  It had attempted to install the bootloader on /dev/sda2 and /dev/sdb2.  I moved on since it would not let me fiddle with the settings and I got the machine rebooted with the rescue option on the iso used for installing.  Now, I can see the root partition is populated with files as expected.  dpkg  will list that linux-image-generic, headers, and linux-generic are installed with other supporting kernel packages.  grub-pc is installed as well.  However, the /boot partition or /dev/md1 was empty initially after the reboot.

**What is the procedure to get grub to install the bootloader on /dev/sda2 and /dev/sdb2, which represent /dev/md1 or /boot?**

Running apt-get update and apt-get upgrade installed a newer kernel and this populated the /boot partition.  Running update-grub results in a "/usr/sbin/grub-probe: error: no mapping exists for 'md2'".  grub-install /dev/md2 or grub-install /dev/sda2 gives the same error as well.  Both commands indicate that **"Autodetection of a filesystem module failed, Please specify the module with the option '--modules' explicitly"**.  What is the right modules that need to be loaded for a raid partition in initrd?  Should I be telling grub to use the a raid module?

Thanks for the help!

---

### Post by oldfred on 2010-08-27
If you are removing raid you also need to remove some meta data on the drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

