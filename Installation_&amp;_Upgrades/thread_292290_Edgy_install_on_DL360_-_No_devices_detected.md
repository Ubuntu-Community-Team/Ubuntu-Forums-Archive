---
title: "Edgy install on DL360 - No devices detected"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by irv075 on 2006-11-03
Hi,

I've been trying to install Edgy on a Compaq DL360 G1. I'm using the on board SmartArray controller fitted with 2 18gb disks. The drives are configured as 2 separate disks i.e. no RAID.

When I use the installer and get to the Prepare Disk Space page I am given the following options:

Erase entire disk: /dev/ida/c0d0 - 0B0 Compaq Smart Array
Manually edit partition table

If I select the first option then continue to install, I get an error saying "No root file system is defined"

If I choose the second option then the partitioner reports "No devices detected"

I've seen other posts about problems with these machines, but those were about not being able to boot after installing.

Any ideas would be greatly appreciated.
Thanks

---

### Post by skotl on 2006-11-03
Hi there,

there's quite a bit of info on this topic in the forums; just search for "proliant".

However, to save you some time the issue is with the cpqarray driver not being loaded. Check [http://www.ubuntuforums.org/showthread.php?t=255335](http://www.ubuntuforums.org/showthread.php?t=255335) for more info.

Cheers,
   Scott

---

### Post by irv075 on 2006-11-04
Scott,

Thanks for the reply. I might be reading it wrong, but is the post you refer to not concerning the server not booting *after* installation? I can't even get that far!

Is there a way to force it recognise the disks when booting into the live cd?

---

