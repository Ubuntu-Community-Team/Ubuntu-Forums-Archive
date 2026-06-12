---
title: "Problem Upgrade Server to Feisty with root on LVM on RAID"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by xtopher.brandt on 2007-05-08
I've seen a lot of threads here about problems upgrading from Edgy to Feisty when a raid was involved. But I can't quite map those problems and solutions to my scenario. Part of the reason is that I'm relatively new to Linux.

To set the stage, I used this wiki article to get my Edgy server set up with a two disk RAID1 ([https://help.ubuntu.com/community/Installation/LVMOnRaid)](https://help.ubuntu.com/community/Installation/LVMOnRaid)). Note that my server boots with LILO, not GRUB.

That all worked great in Edgy. The upgrade to Feisty had no problems. During the upgrade it did ask a question about raid volume (mount order?). I took the default (all), as it seemed to be the correct option at the time.

It failed on restart (of course, or I wouldn't be here). The failure seems to occur when its trying to mount the volume group. The raid gets assembled ok and then the boot stops for about 5 minutes, after which it times out and drops to the BusyBox shell. 

mdadm reports that the raid is assembled and in good condition (/dev/md0). It's comprised of /dev/sda and /dev/sdb1. 

lvm reports that the VG is there and in good condition.

From BusyBox when I try

[INDENT]mount -t ext3 /dev/md0 /root[/INDENT]

as was suggested in another thread. I get an error Device or Resource Busy (not 100% sure if I got the message wording correct). So it seems that LILO is timing out waiting to mount my LVM. 

One other note; just before LILO pauses for the 5 minute timeout there is an error that seems to be associate with binding. I'm not clear on what that error is (the report says -16), or what **binding** even is.

So I'm stuck. I've downloaded the 7.04 server disk, but the rescue mode on it dies at about the same point (I havn't left it to see what happens after it times out).

Any help would be greatly appreciated.

Chris.

---

### Post by xtopher.brandt on 2007-05-10
Could someone throw me a bone. I'm dead in the water here.

I have one update. The 7.04 server rescue disk does eventually time out and I can mount my lvm from there. But what do I need to change to get it work on a regular boot? How do I diagnose the problem?

Help
Chris

---

