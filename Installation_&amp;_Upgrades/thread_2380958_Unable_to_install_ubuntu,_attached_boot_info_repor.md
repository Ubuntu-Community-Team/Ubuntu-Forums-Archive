---
title: "Unable to install ubuntu, attached boot info report"
date: 2017-12-24
forum: Installation &amp; Upgrades
---

### Post by akshay58165 on 2017-12-24
I am unable to install ubuntu or any distro. please look into my boot repair report below

[http://paste.ubuntu.com/26245457/](http://paste.ubuntu.com/26245457/)

---

### Post by oldfred on 2017-12-24
Looks like you had it installed as you still have the UEFI boot entries.
But UEFI retains entries unless you manually houseclean.
And Boot-Repair will find all the .efi boot files in ESP - efi system partition and create a large 25_custom with all those entries. Most do not need that or can houseclean most of the entries out.

The errors on sda3 are not valid, the system reserved is a required unformatted partition by Windows.
Do you have a mmcblk drive,SD card? I would just unplug it for now, not sure why it is showing errors.
But sda4 not seen which is typical of Windows fast start up or hibernation is on.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Even if you turned fast start up off before, Windows updates may have turned it back on.

Delete old UEFI boot entries, you also should delete old folders in ESP.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

