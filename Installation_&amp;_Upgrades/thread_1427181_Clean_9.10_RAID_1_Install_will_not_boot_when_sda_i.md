---
title: "Clean 9.10 RAID 1 Install will not boot when sda is removed"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by jackmetal on 2010-03-11
I performed a clean install of 9.10 via the Alt-CD and configured my 2 x 500G drives in a RAID 1 configuration, installed and booted fine after the install.  With both drives connected, everything works perfectly; when I remove sda to test my raid install booting off the other drive (sdb), it does not boot and drops me into busybox.  When I reconnect sda back, it again boots up fine.

When I look at my raid config, everything appears fine to me:
mdadm --query --detail /dev/md0
```
/dev/md0:
        Version : 00.90
  Creation Time : Tue Mar  9 17:46:27 2010
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 11 06:56:47 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 3e822449:e39681a5:9fd17548:b987b8a9
         Events : 0.6435

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
```

cat /proc/mdstat
```
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      488383936 blocks [2/2] [UU]
      
unused devices: <none>
```

I saw grub install to both sda and sdb at the end of the install and verified the device map:
cat /boot/grub/device.map
```
(hd0)	/dev/sda
(hd1)	/dev/sdb

```

So far, everything I've looked at appears fine, so I'm unclear on where to look next.

--edit--
I've also manually installed grub to both sda and sdb again, (just to be sure) and I still get the same results.  Boots fine with both sda and sdb installed, does not boot with sda removed but boots fine again when sda is re-installed.  With sda pulled out, I see grub come up and then shortly afterwards it drops me into busybox.

Thanks very much for the help!

---

### Post by darkod on 2010-03-11
Even though you saw grub get installed to both disks, as first try I would make sure grub is actually installed on /dev/sdb. And looking at the right place for the grub config files.

Although I think busybox comes fater grub. If grub is not there you should get "no OS present" or similar message. But I don't have any other ideas.

---

### Post by jackmetal on 2010-03-11
ok, I've done further testing:

It appears that it will not boot when the RAID 1 is in degraded mode.  No matter which disk I pull (sda or sdb), it will not boot if only 1 is connected.  If both are connected (even if I swap cables between sda and sdb) it boots fine!  

I've verified my /etc/initramfs-tools/conf.d/mdadm file:
```
BOOT_DEGRADED=true
```

When it drops me into busybox, I have the following displayed:
```

file descriptor 3 left open
Volume group "vgroot" not found
Check cryptopts=source= bootarg cat /proc/cmdline 
or missing modules,devices cat /proc/modules ls /dev -r 
ALERT! /dev/mapper/vgroot_lvswap does not exist. Dropping to a shell!

```

From that, it appears the Alt-CD install missed something (maybe the lvm module or dm_crypt?)..   But if it did, it's really weird that it boots fine with both drives connected and NOT when either one is pulled.

Any ideas?

Thanks a lot for the help!

--edit--
Luckily this is only a test machine for me, and I wanted to play around with Ubuntu and RAID a bit..  It worked fine under ArchLinux, so in the meantime I'm going back to Arch on this one!   If anyone has any ideas, please let me know and I'll try Ubuntu out again.

Thanks!

---

### Post by psusi on 2010-03-11
Try using mdadm to recognize and activate the array from the busybox prompt.  Something like mdadm -D /dev/md0 to check the status or mdadm --assemble --scan to detect and activate arrays.  If you get the array activated you should be able to exit and the boot will continue.

Oh, and after you set BOOT_DEGRADED to true, did you update your initramfs so it took effect?

---

### Post by jackmetal on 2010-03-11
Thanks for the tips..  Yes, I had manually updated my initramfs and I also did a pkg-reconfigure on mdadm.

I've found where the issue is, but I haven't reconfigured like I had it in order to find the actual resolution.

I took encryption out of the configuration and it works fine (with either disk missing).  So it appears that encrypted swap and home were 'somehow' the issue.  ??  I'll try it again if I can figure out what the issue actually is.

This time I have 2 x 500G drives in a RAID 1 configuration, with everything LVM (and it works perfectly).  Earlier, I had the same configuration except I had swap and home encrypted.  It's just really weird that encryption worked perfectly with both drives in, but caused the issue when one of the drives were pulled out.  Very Strange!!!

---

### Post by tonywhelan on 2010-10-22
Same problem, same conclusion. Ubuntu simply does not handle encrypted raid, despite giving the impression that it does. Very irritating that there is no apparent interest in remedying this.

---

