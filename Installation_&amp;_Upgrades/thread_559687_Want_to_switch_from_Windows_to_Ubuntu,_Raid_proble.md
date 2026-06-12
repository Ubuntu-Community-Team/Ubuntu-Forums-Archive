---
title: "Want to switch from Windows to Ubuntu, Raid problems"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by CooLSpoT on 2007-09-25
This is my first time trying to get off of Windows for my server.

Problem: trying to install Ubuntu on my Raid 5 setup.

I am trying to use dmraid that comes bundled in ultimate Ubuntu, and I have made my way through the problems upto this point. Google has failed me, so here it goes:

After I install dmraid and load it up to create my raid, I am getting this 

Error message:
root@ubuntu:/home/ubuntu# dmraid -ay
ERROR: device-mapper target type "raid45" not in kernel
root@ubuntu:/home/ubuntu# 

I also also tried mdadm, but not getting anywhere on that, Any input is welcome, even if you think I should go back to windows.

---

### Post by networkr on 2007-09-25
Strange, you did not mention what hardware for RAID you were using.  I have tested several on-board RAID chipsets and have had mixed results.  In the end, I went with a hardward RAID implementation that involved upgrading the RAID controller to 3-Ware RAID 5 controllers.  Linux sees them at time of install, so no special config is required.  I have had great reliability and usability on numerous Linux / BSD installs and haven't looked back ever since.

RAID hardware controllers are kinda like modems used to be in Linux.  The way it used to be before support for Win-Modems, Linux wanted full blown controller-based dial-up modems or it didn't work.

It works similarly with RAID controllers, Linux wants a RAID controller that doesn't borrow system resources to accomplish it's task, similar to what the win-modems used to do.  I know for a fact many on-motherboard Promise RAID controllers don't work with Linux, and it's for those same reasons, borrowing system resources.

3-Ware controller cards overcome all these obstacles and work perfectly with Linux.

Cheers,

networkr

---

### Post by david3d on 2007-09-25
Well I had to look up what the "ultimate" version of Ubuntu is and for a server I would say far way from that.  Stick to the main line especially for servers.  If you need raid use the alternative installer which supports both dmraid and lvm in the installer.

Now on to the raid problem.  I'm going to suggest a few things but would advise you to be careful and if you have any questions please ask before doing anything that may risk your data.

First you need to try to figure out what's going wrong.  So what error(s) if any are you getting when you try to start the array?  Any thing of interest in the dmesg output or in the /var/log/messages or /var/log/kern.log?  Do you have dm_mod and the appropriate raid level modules loaded?

Next I would double check the partition type on your drives/partitions that are involved in the raid set using fdisk or cfdisk.  Make sure they are marked as "'fd'  Linux raid auto" you can safely change the partition type here without effecting any data on the partition.  This assists in the automatic detection and assembly of the arrays.  If the partitions weren't set as the correct type try to start your array's after making these changes.  You may need to reboot for some of the partition tables to get updated.

If that doesn't sort out your problems then the next thing is to have a look at the metadata on each drive/partition that's involved to see what each partition thinks should be happening.  This is done using the following command "mdadm --misc -E /dev/sda1"  replace the device with the appropriate devices in your system.  Each partition's metadata should contain the information about all the other devices in the array.  Make sure all of these think they are part of the same array etc.

Armed with that information we should be able to start exploring some assembly options.  Before you proceed make note not to use mdadm --create.  Doing so could wipe out the existing arrays and their data.  If all the metadata is intact then try using the assemble options.  See mdadm --assemble --help for all the options.  This should get the device going again.  If the metadata is missing or corrupted then you can force things together in most cases using the build options.  Check out mdadm --build --help for more details before proceeding.  But its basic usage is as follows.

mdadm --build /dev/md0 -l5  -n3 /dev/sdb1 /dev/sdc1 /dev/sdd1

This will force together a raid 5 device ( -l5 ) made up of 3 devices ( -n3 ) using partitions sdb1, sdc1, sdd1

Hope this helps you sort out your problems and if you have any questions it's better to ask here before risking any data loss.
-
David

---

