---
title: "Ubuntu dual boot Cloning: ALERT! /dev/disk/by-uuid/xxxxxxxxxx does not exist..."
date: 2017-11-04
forum: Installation &amp; Upgrades
---

### Post by theexpert1234 on 2017-11-04
Hi Everyone ,

I have recently cloned dual boot Win7 and Ubuntu14 LTS  from HDD to SSD  with Acronis . I am able to boot WIN7 fine  but having issues with  ubuntu booting with following error

**************************************************   **************************************************   ******************************
error: no such device: 3892DDC792DD8A30 .
Loading Linux 3.13.0-112-generic ...
Loading initial ramdisk ...

Press any key to continue...


Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/3892DDC792DD8A30 does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a lost of built-in commands.
(initramfs)
**************************************************   **************************************************   ******************************

I have tried to repair GRUB 2 with Ubuntu live USB and the error is still there! .  Following link is the  boot info.

[http://paste.ubuntu.com/25884944/](http://paste.ubuntu.com/25884944/)

from the boot info ,I can see the UUID "3892DDC792DD8A30" almost 95 times   which I believe is my old  HDD partition UUID .

from my beginner knowledge perspective I believe If the old HDD  partition UUID is replaced by new device SSD partition UUID  it may start bootup correctly , but not sure which partition UUID to use  and how to do it ?.

Could you please see the bootinfo and advise, your comments are welcome!.

---

### Post by vasa1 on 2017-11-04
Please don't post the same issue in different sub-forums.

Re-opened at poster's request and closed the other one ([https://ubuntuforums.org/showthread.php?t=2376620](https://ubuntuforums.org/showthread.php?t=2376620)).

---

### Post by yancek on 2017-11-04
First, you have a 'WUBI'' install which basically installs Ubuntu inside a windows partition and runs it as a program inside windows similar to virtualization software.  WUBI has not been supported for several years and is no longer being developed and is not expected to work on any windows newer than windows 7.

Since you have windows 7, it should work so which drive is the original and which is the cloned?  You have a 465GB drive (sda) which shows all windows partitions with the Ubuntu Wubi on sda5.  sdb looks like a flash drive and sdc is a 298GB drive with only one windows partition.  Is sdc the drive you cloned to because if it is, there is no sign of Ubuntu on it? 

The UUID you post beginning with "3892..." only appears in the grub.cfg file from sda5.  There is no sign of this UUID in the blkid output and in fact no UUID's show for sdc.  If sda is the drive you cloned TO, you could replace the UUID beginning with "3892..." in the grub.cfg file on sda5 with the UUID listed in your output for sda5 "07F84A9524ADA60E".  I'd just do the first menuentry and reboot to test, don't update grub.  If sdc is the drive you cloned TO, this obviously won't work.

So which drive is the cloned FROM and which is the cloned TO.  sdc doesn't show much, one partition with unknown filesystem type?

---

### Post by oldfred on 2017-11-04
You are showing a wubi install, that has not been supported since 12.04.
And your install seems to be 14.04.2 so not sure how you installed wubi, although is was available, but not supported, nor recommended.
Wubi is actually a large file root.disk inside your NTFS partition. 

I do not know and have never used wubi.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

I also have recommended that rather than try to clone Ubuntu to a new drive, just reinstall. It also then is a good test of your backup procedure, and if backup recovery is not exactly what you want, you have to old drive to recovery more data or settings from (and then fix backup procedure).
But to install Ubuntu you need Linux formatted partition(s), but you only have NTFS Windows type.

---

### Post by theexpert1234 on 2017-11-04
Hi,

The 465GB drive (sda) is the "cloned TO" SDD and connected as my primary drive to SATA port of my laptop, I think we can  **ignore** sdb (as it was Usb bootable device for Ubuntu 17 for GRUB repair) and sdc ( it was USB backup external 298GB drive,just for data backup), so i can unplug the drives sdb and sdc if required.(The "cloned from" was HDD mechanical drive which I replaced with SSD on SATA port of my laptop , I am  keeping HDD drive intact and waiting to solve this issue) 

I was of the  idea to just update the  grub.cfg file on sda5 with the UUID listed in the output for sda5 "07F84A9524ADA60E", but as I am beginner, I dont know the step by step procedure to update the file and also dont know how to do the first menuentry and reboot to test,and  don't update grub?.... Can I update the grub.cfg file when I have booted with  Ubuntu 17 LTS bootable USB ? or I can do that from any other method as well?

Also regarding the Wubi , I installed Ubuntu12.0x first through the Windows 7 and then upgraded via internet connection from 12.ox to Ubuntu14.04 LTS, but I think Wubi is only supported uptill 12 but not 14.That makes a bit complex as I have no Linux formatted partition and all NTFS formatted partition , If I want to install a new Ubuntu now then I would need to reformat from NTFS to Linux partition format and I will loose all my installed programs in ubuntu , which I didnt wanted to.....




> **yancek said:**
> First, you have a 'WUBI'' install which basically installs Ubuntu inside a windows partition and runs it as a program inside windows similar to virtualization software.  WUBI has not been supported for several years and is no longer being developed and is not expected to work on any windows newer than windows 7.

Since you have windows 7, it should work so which drive is the original and which is the cloned?  You have a 465GB drive (sda) which shows all windows partitions with the Ubuntu Wubi on sda5.  sdb looks like a flash drive and sdc is a 298GB drive with only one windows partition.  Is sdc the drive you cloned to because if it is, there is no sign of Ubuntu on it? 

The UUID you post beginning with "3892..." only appears in the grub.cfg file from sda5.  There is no sign of this UUID in the blkid output and in fact no UUID's show for sdc.  If sda is the drive you cloned TO, you could replace the UUID beginning with "3892..." in the grub.cfg file on sda5 with the UUID listed in your output for sda5 "07F84A9524ADA60E".  I'd just do the first menuentry and reboot to test, don't update grub.  If sdc is the drive you cloned TO, this obviously won't work.

So which drive is the cloned FROM and which is the cloned TO.  sdc doesn't show much, one partition with unknown filesystem type?

---

### Post by theexpert1234 on 2017-11-04
Hi,
I have another update regarding this issue!!, I just tried to clone again over last night , this time with the Clonezilla(A linux based cloning software) , and now both WIN7 and Ubuntu 14 LTS are working really fine with no booting issues. I think in order to clone a linux based dual boot system some linux based cloning software like Clonezilla is good option, Its not hard to Clone but there is a bit more configuration and care required in Clonezilla than Acronis .. youtube has good videos regarding these!!. thanks to the everyone for the support in this regards!!

---

### Post by oldfred on 2017-11-04
Still recommend you back up your data and do a full partitioned install of Ubuntu.

Even the developer of Wubi expected users to install a full Ubuntu with the next semi-annual release. It was just for a test install to try it out.

---

### Post by theexpert1234 on 2017-11-04
Well, Its also on my plan to migrate it to a Linux partition...not sure if there is  a workaround to keep my existing programs installed even after migration...normally 0% chance I think unless some expert advise otherwise..

> **oldfred said:**
> Still recommend you back up your data and do a full partitioned install of Ubuntu.

Even the developer of Wubi expected users to install a full Ubuntu with the next semi-annual release. It was just for a test install to try it out.

---

### Post by oldfred on 2017-11-05
If wubi is working, you can copy its /home to your new install whether you have /home as a separate partition or not.
Your /home has all your user settings and data.

You can export a list of installed apps and use that to reinstall them.
If installing in a newer version, best to manually edit out kernels, and a few apps may not be available in new version.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

