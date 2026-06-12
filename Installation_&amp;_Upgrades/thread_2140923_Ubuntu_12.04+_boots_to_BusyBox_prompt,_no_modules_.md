---
title: "Ubuntu 12.04+ boots to BusyBox prompt, no modules loaded"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by chipbuster on 2013-05-01
Hey all. First off, sorry if this post is a little disorganized. I've been working on this problem for a while and I am quite tired.

I'm trying to install any recent Ubuntu onto a Thinkpad X220 which has a secondary mSATA SSD (trying to install to the mSATA). I had 12.04 (both Ubuntu and Kubuntu) working on this thing at some point in the past, and all I did for the installation was to let the autopartitioner do the work.

Recently, I made a major oopsie and decided to try to install Ubuntu 13.04. Lo and behold, when I tried to boot out of my install, it dropped me into a busybox prompt. The error message seems fairly typical based off of the searches I've been doing:

```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/[uuid] does not exist. Dropping to shell!
```

After checking in the livedisk to make sure that the uuid's matched, trying the rootdelay trick (where you set rootdelay=90 and hope for the best) and trying to edit the boot arguments to use /dev/sdX notation instead, I noticed that in the busybox prompt, I couldn't find any of my drives: the command ```
ls -a /dev/sd*
``` was returning a blank result. Similarly, ```
cat /proc/modules
``` is showing blanks as well.

Although I should have known better at this point, I tried to use the live version to create a different initramfs. By using some combination of lsmod, awk, pipes, and redirection (I can't remember exactly what at this point), I managed to copy all the kernel modules that were loaded in the liveOS over to the /etc/initramfs-tools/modules on the SSD. Chrooted in, used update-initramfs to update the file. Confirmed that it was about 50% larger than the default one, and rebooted. Still nothing: no modules loaded, no sd* devices.

At this point, I really have no clue where to go. I'm particularly confused because at one point, I was able to install 12.04 on this thing without even touching the partitioning, but now it seems I won't be able to get this going without some serious work :icon_frown:. If anyone can nudge me in the right direction, I'd really appreciate it.

Additional information:

I have also tried the boot-repair toolkit to no success. It appears that the program hung while trying to upload the pastebin, since the URL I got keeps giving "unknown paste" on the website. If anyone thinks its worth trying again, I'll do that.

Final three lines of dmesg before the hang (without times) are:

```

udevd[63]: starting version 175
Refined TSC clocksource calibration: 2790.934MHz
Switching to clocksourse tsc
```

---

### Post by dino99 on 2013-05-01
to check the real uuids: ```
 sudo blkid 
```
check that the bios/uefi is booting on the good disk
then boot on the recovery mode and choose "root" to update grub : ```
sudo dpkg-reconfigure grub-pc 
```

---

### Post by chipbuster on 2013-05-01
UUIDs look good from the LiveOS, but I can't do that from the BusyBox because there are no disks. I can't boot into recovery mode either--the same thing happens:I get dumped into a BusyBox without any disks or modules.

---

