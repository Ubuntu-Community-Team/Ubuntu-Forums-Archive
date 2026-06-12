---
title: "BusyBox v1.1.3 Boot Issue"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Mr.Zim on 2007-11-04
I was using my Ubuntu rig running 7.10. A power surge/power outage occured for ~5 seconds. My computer turned off. Upon boot, I get the following (after ALT+F1):
> 
Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/595861b1-2941-4d00-bab5-d44c0d2c77d9) = hada5(3,5)
kinit: trying to resume from /dev/disk/by-uuid/595861b1-2941-4d00-bab5-d44c0d2c77d9
kinit: No resume image, doing normal boot...
mount: Mounting /dev/disk/by-uuid/c45df572-afc4-4e6b-974f-37c8dd167400 on /root
failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
Target filesystem doesn't have /sbin/init

How can I fix this? Recovery mode doesn't boot either, but I can boot into a Live CD. I have checked, and the GRUB file does point to the kernel. How can I fix this?

---

### Post by stitheridge on 2007-11-05
I have the same problem (Kubuntu 7.10), but it wasn't started by a power failure. I applied a bunch of updates through apt today, booted to Windows, did some stuff and tried to reboot to Kubuntu. At first the problem was transient, occurred 50% of the time but now is consistent after a few reboots.

The text I can see is:
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
Target filesystem doesn't have /sbin/init

I can't see any text above this on the output though

 I run Kubuntu dual boot XP.

Any thoughts would be appreciated!

Thanks

S

---

### Post by stitheridge on 2007-11-05
Sorry, ignore my reply to Mr Zim. Similar error message but it was self inflicted. I b0rked my fstab file with a "minor" tweak that I forgot about. Fixed now.

Best of luck Mr Zim.

---

