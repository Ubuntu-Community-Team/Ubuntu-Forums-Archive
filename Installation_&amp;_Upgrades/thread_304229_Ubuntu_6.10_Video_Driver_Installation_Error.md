---
title: "Ubuntu 6.10 Video Driver Installation Error"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by r-486 on 2006-11-21
I'm trying to install Ubuntu 6.10, but cannot due to hardware issues. I have an X800 XL video card and a Samsung SyncMaster 997DF monitor. I've tried the Desktop and Alternative disk with no success.

When I try the command “apt-get install xorg-driver-fglrx” I get the following error:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

I tried "apt-get update", but I get the following on both the Live and Alternate version:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
E: Some index files failed to download, they have been ignored, or old ones used instead.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

It appears that I'm not connected, because I just tried pinging some hosts and none of the packets got sent.

How can I connect to the internet and go through the authentication process if possible?

When I try the command “dpkg-reconfigure xserver-xorg”, I tried the default ATI driver with no success. I've tried the VGA driver, and it didn't work as well. Next, I tried the VESA driver, but the monitor goes completely black after trying the command “startx”.

With the other drivers I get the following error after using the command “startx”:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
Fatal Server Error:
No screens found
Fatal IO Error 104
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

I've also tried graphics safe mode.

---

### Post by r-486 on 2006-11-21
I already edited the /etc/X11/xorg.conf file to include the vesa driver but the monitor goes black just as it does when I try changing the driver by using the command "dpkg-reconfigure xserver-xorg".

I downloaded the official ATI driver "ati-driver-installer-8.31.5-x86.x86_64.run" to my USB flash drive. I ran "fdisk -l" and it detects my USB flash drive as /dev/sdd.

I ran "sh ati-driver-installer-8.31.5-x86.x86_64.run", but I get the following error:
sh: Can't open ati-driver-installer-8.31.5-x86.x86_64.run

I tried the command "/dev/sdd and /dev/sdd1" and I get the following error:
-bash: /dev/sdd: Permission denied

I tried the change directory command "cd /dev/sdd", but it didn't work and I'm not sure if that's even correct.

I'm using my university's ISP so that could possibly be the reason why I'm not connected.

---

### Post by r-486 on 2006-11-21
I just figured it out! I edited the xorg.conf file by replacing ati with radeon.

---

