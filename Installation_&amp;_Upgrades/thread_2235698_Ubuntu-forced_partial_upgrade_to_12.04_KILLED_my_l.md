---
title: "Ubuntu-forced partial upgrade to 12.04 KILLED my laptop"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-22
DELL VOSTRO 3500 running Ubuntu 12.04 64-bit with HWE upgrade done

UBUNTU demanded a partial upgrade around 1100 hrs EDT.  Fortunately, I backed up everything.

PC rebooted with ERROR @wl_cfg80211_scan : WLC_SCAN error (-22).

Please note that WIFI is not in use.  There has not been any hardware changes.  Things that fixed similar error in January 2014 have not worked.

MISSION CRITICAL PC IS DOWN

Perhaps the gurus of Ubuntu will send a fix.

John

---

### Post by cigtoxdoc on 2014-07-22
ADDITIONAL INFORMATION:

Partial upgrade removed ubuntu-desktop and all related applications

Reinstalled ubuntu-desktop.  System willl only boot to CLI.  When I log in and do sudo lightdm service start, there is no desktop. but a number of messages, most with OK at the end, but starting load fallback graphics devices gives a "fail".

John

---

### Post by kansasnoob on 2014-07-22
Yep, that HWE upgrade was a mess:

[http://ubuntuforums.org/showthread.php?t=2234260](http://ubuntuforums.org/showthread.php?t=2234260)

[http://ubuntuforums.org/showthread.php?t=2234815](http://ubuntuforums.org/showthread.php?t=2234815)

[http://ubuntuforums.org/showthread.php?t=2234813](http://ubuntuforums.org/showthread.php?t=2234813)

[http://ubuntuforums.org/showthread.php?t=2234830](http://ubuntuforums.org/showthread.php?t=2234830)

[http://ubuntuforums.org/showthread.php?t=2234693](http://ubuntuforums.org/showthread.php?t=2234693)

[http://ubuntuforums.org/showthread.php?t=2234922](http://ubuntuforums.org/showthread.php?t=2234922)

[http://ubuntuforums.org/showthread.php?t=2234729](http://ubuntuforums.org/showthread.php?t=2234729)

[http://ubuntuforums.org/showthread.php?t=2235159](http://ubuntuforums.org/showthread.php?t=2235159)

[http://ubuntuforums.org/showthread.php?t=2235287](http://ubuntuforums.org/showthread.php?t=2235287)

[http://ubuntuforums.org/showthread.php?t=2235698](http://ubuntuforums.org/showthread.php?t=2235698)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320)

At this point I think the only reasonable thing to do is back up any important data/profiles/etc and perform a fresh install of Trusty :(

But those who dual-boot need to also beware of this installer bug that eats everything during re-installation:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Then in the future avoid those HWE stacks like a plague - that is; be sure to install using the LTS images with the OEM kernel and X-stack (eg: 12.04, 12.04.1, 14.04, and 14.04.1):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.LTS_Kernel_Support_Schedule)

---

### Post by bapoumba on 2014-07-22
The upgrade is problematic to some users, please see here if some of the actions could apply to your situation : [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264)
> Only installing the original precice Xstack (xserver-xorg-lts-precise), which removes the current xstack and after that installing the trusty xstack in one step without restart, works.

---

### Post by cigtoxdoc on 2014-07-22
After all I have read, it appears that keeping 12.04 will be continuing grief.  Is upgrading to 14.04 the solution?

John

---

### Post by bapoumba on 2014-07-22
Yes it is.

---

### Post by cigtoxdoc on 2014-07-22
Thank you very much.  All my PCs are dual boot.  Do I have to worry about 14.04 install wiping out my NTFS partitions?

John

---

### Post by bapoumba on 2014-07-22
There is a bug linked in my sig you need to be careful about, please read it. The wording in the installer can be confusing.
Note your partitions down, all the ones you want to keep. For ex here, I do not have a separate /home (used to for years, but that is a test box), root is on /dev/sda1, others are for storage with all my stuff and a spare one for Utopic :
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f80fafa7-7325-4697-9fdc-610f0746c80e /               ext4    errors=remount-ro 0       1
# /storage was on /dev/sda5 during installation
UUID=f606ac2b-b8c8-4e99-9b7f-26f565c511c6 /storage        ext4    defaults        0       2
# /storage1 was on /dev/sda8 during installation
UUID=82809672-bd1e-4d0d-a1e0-839241e809d7 /storage1       ext4    defaults        0       2
# /utopic was on /dev/sda7 during installation
UUID=c7a25049-f435-4704-9b7e-2014f66fafe8 /utopic         ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a6c9d280-3b7b-4c24-9ca8-563b1b23a38f none            swap    sw              0       0

```

Once the installer gets to the partition scheme, choose "do something else" and choose your root partition, mount it to / and tick format it (from last install memory, the wording may be different). If you have a separate /home, do the same to mount it as /home and you can leave the format box unticked if you want to keep it unchanged (maybe a good idea, may be not as your user config files will be preserved and may conflict with newer ones). Choose the swap as swap.

In my case, I would leave sda5, 7 and 8 alone, as I want to keep my own files and spare partition unchanged.
Your windows partition should show up here, so you'll know which one it is. Please post your fstab if you want we have a look at it.

---

