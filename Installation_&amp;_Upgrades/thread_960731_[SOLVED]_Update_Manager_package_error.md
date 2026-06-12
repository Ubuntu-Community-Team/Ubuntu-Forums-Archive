---
title: "[SOLVED] Update Manager package error"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by MikeyDL on 2008-10-27
Recently I tried to install a normal update with update manager.  I downloaded the files into a deb pacakge but get the following error when it tries to run:

E: /var/cache/apt/archives/gcc-4.2-base_4.2.4-1ubuntu3_i386.deb: failed in buffer_read(fd)

I've manually removed (deleted) the deb file and redownloaded but I get the same error.  Any ideas why i'm getting the error?

Thanks!

---

### Post by lemming465 on 2008-10-28
Do you have any disk errors listed in /var/log/messages?  Maybe run "sudo apt-get clean" to purge the cache and then retry the update-manager?

---

### Post by ciscosurfer on 2008-10-28
i/o errors are usually indicative of one or more things: a failing drive, data attempting to be written to the drive faster than the system can handle, a locking handle or other file that may be "corrupt", or lack of free space on the partition or drive.  If you're certain you have free space and your drive is healthy, then read on.  Otherwise, make sure you have enough free space```
df -h
``` and that your disk isn't on its last legs```
sudo apt-get install hdparm
man hdparm

sudo apt-get install smartmontools
man smartctl
```For example, to test the overall health of your drive```
sudo smartctl -H /dev/sda

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```First, check out [this page on launchpad]("https://answers.launchpad.net/ubuntu/+source/dpkg/+question/22587").  Read the whole page.  Pay particular attention to the last post on that page.  Now, let's augment what was said there for your scenario:

   You can try the following.  Go ahead and **cat** this file```
cat /var/lib/dpkg/info/gcc-4.2-base.list
```Normally you'd get a list of files included in the **gcc-4.2-base** package, but this time you'll likely get an empty list or an error alerting you that there is a problem with the file.  Perhaps something along these lines: failed in buffer_read(fd)

 A possible solution might be to remove this list file```
sudo rm /var/lib/dpkg/info/gcc-4.2-base.list
```You should now be able to run these commands and then either manually to let your package manager download and install/upgrade gcc or you can download the .deb and install it yourself```
sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

