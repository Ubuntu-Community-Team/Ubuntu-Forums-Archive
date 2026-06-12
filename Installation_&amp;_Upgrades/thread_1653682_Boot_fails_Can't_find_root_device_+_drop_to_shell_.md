---
title: "Boot fails: Can't find root device + drop to shell (Softraid/0 on Ubuntu 10.10)"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by ErikDeBruijn on 2010-12-27
From one day to the other my system stopped booting properly. Since I (finally) fixed it, I wanted to share my solution. It runs on a fakeraid pair of SSD's of 60 GB each (actually a single Revodrive device, but it shows up as two devices). When Ubuntu 10.10 boots, I'm dropped to a shell.

During boot, when I removed "silent splash" from the kernel's command line, I got these messages:
```

[    4.960240] scsi 6:0:0:0: Direct-Access     ATA      OCZ-REVODRIVE    1.20 PQ: 0 ANSI: 5
[    4.960425] sd 6:0:0:0: [sdg] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.960454] sd 6:0:0:0: Attached scsi generic sg7 type 0
[    4.960607] sd 6:0:0:0: [sdg] Write Protect is off
[    4.960668] sd 6:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    4.960686] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.960859]  sdg: sdg1 sdg2 < >
[    4.961317] sdg: **partition table partially beyond EOD, enabling native capacity** (EOD means end of device, I think is safe to assume)
[    4.961571]  sdg: sdg1 sdg2 < >
[    4.961970] sdg: **partition table partially beyond EOD, truncated**
[    4.962080] sdg: p1 size 230468608 **extends beyond EOD, truncated**
[    4.962208] sdg: p2 start 230469118 is beyond EOD, truncated

```
When dropping to a busybox shell, it says: 
```

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a0c70.....1c4d4 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```

I *could* boot from the USB boot device that I created from a CD image. When using the same kernel that didn't work on my installation, the USB drive would boot. So it definitely had to do with my installation, not in principe with the (fake)raid array.

I've tried MANY MANY things. After a long search I found that the "dmraid" package wasn't installed. So I did the following:
I booted from the CD. The FakeRaid array showed up as 
[B]# mkdir /mnt
# mount /dev/mapper/sil_asdfasdf1 /mnt
[/B](where asdfasdf is the actual name of the first partion on the array)
[B]# mount --bind /dev/ /mnt/dev
# mount --bind /proc/ /mnt/proc
# mount --bind /sys/ /mnt/sys
# chroot /mnt

# apt-get install dmraid[/B]
I had also added these lines to: /etc/initramfs-tools/modules:
```
raid0
dmraid
md-raid0
```
However, I doubt that this is what was needed (as I had that already when it didn't work, but I might be required in addition to installing dmraid)
**# update-initramfs -a**
After installing this, the problem was solved!! This is strange since I don't recall uninstalling this package or changing anything important, for that matter (perhaps did apt-get upgrade, but that's about it!).

If this doesn't help, try adding rootdelay=90 to your kernel command line (from grub), if it works, make it permanent as explained here:
[http://ubuntuforums.org/showthread.php?t=981159&page=2](http://ubuntuforums.org/showthread.php?t=981159&page=2)

My problem shows some similarity to this: [http://ubuntuforums.org/showthread.php?t=1026461](http://ubuntuforums.org/showthread.php?t=1026461)

---

### Post by k66473 on 2010-12-30
This issue has just happened to me.

When gave up.... message appears, I type exit several times and the system load fine.

But I will try this solution in this evening.
Regards,

---

### Post by HankB on 2011-03-21
Thanks for posting this. I had a similar problem installing to md-raid. I posted at [http://ubuntuforums.org/showthread.php?t=1711681](http://ubuntuforums.org/showthread.php?t=1711681) and cited your post for further information.

best,
hank

---

### Post by piteer1 on 2011-10-13
> **ErikDeBruijn said:**
> From one day to the other my system stopped booting properly. Since I (finally) fixed it, I wanted to share my solution. It runs on a fakeraid pair of SSD's of 60 GB each (actually a single Revodrive device, but it shows up as two devices). When Ubuntu 10.10 boots, I'm dropped to a shell.

During boot, when I removed "silent splash" from the kernel's command line, I got these messages:
```

[    4.960240] scsi 6:0:0:0: Direct-Access     ATA      OCZ-REVODRIVE    1.20 PQ: 0 ANSI: 5
[    4.960425] sd 6:0:0:0: [sdg] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    4.960454] sd 6:0:0:0: Attached scsi generic sg7 type 0
[    4.960607] sd 6:0:0:0: [sdg] Write Protect is off
[    4.960668] sd 6:0:0:0: [sdg] Mode Sense: 00 3a 00 00
[    4.960686] sd 6:0:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.960859]  sdg: sdg1 sdg2 < >
[    4.961317] sdg: **partition table partially beyond EOD, enabling native capacity** (EOD means end of device, I think is safe to assume)
[    4.961571]  sdg: sdg1 sdg2 < >
[    4.961970] sdg: **partition table partially beyond EOD, truncated**
[    4.962080] sdg: p1 size 230468608 **extends beyond EOD, truncated**
[    4.962208] sdg: p2 start 230469118 is beyond EOD, truncated

```
When dropping to a busybox shell, it says: 
```

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a0c70.....1c4d4 does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```

I *could* boot from the USB boot device that I created from a CD image. When using the same kernel that didn't work on my installation, the USB drive would boot. So it definitely had to do with my installation, not in principe with the (fake)raid array.

I've tried MANY MANY things. After a long search I found that the "dmraid" package wasn't installed. So I did the following:
I booted from the CD. The FakeRaid array showed up as 
[B]# mkdir /mnt
# mount /dev/mapper/sil_asdfasdf1 /mnt
[/B](where asdfasdf is the actual name of the first partion on the array)
[B]# mount --bind /dev/ /mnt/dev
# mount --bind /proc/ /mnt/proc
# mount --bind /sys/ /mnt/sys
# chroot /mnt

# apt-get install dmraid[/B]
I had also added these lines to: /etc/initramfs-tools/modules:
```
raid0
dmraid
md-raid0
```
However, I doubt that this is what was needed (as I had that already when it didn't work, but I might be required in addition to installing dmraid)
**# update-initramfs -a**
After installing this, the problem was solved!! This is strange since I don't recall uninstalling this package or changing anything important, for that matter (perhaps did apt-get upgrade, but that's about it!).

If this doesn't help, try adding rootdelay=90 to your kernel command line (from grub), if it works, make it permanent as explained here:
[http://ubuntuforums.org/showthread.php?t=981159&page=2](http://ubuntuforums.org/showthread.php?t=981159&page=2)

My problem shows some similarity to this: [http://ubuntuforums.org/showthread.php?t=1026461](http://ubuntuforums.org/showthread.php?t=1026461)

ErikDeBruijn you're a lifesaver!! :D I lost 3 days looking what's happening that I cannot install kubuntu on my laptop with fakeraid (I need dual boot with windows). Great thanks!

---

### Post by bincue on 2012-01-12
> **ErikDeBruijn said:**
> 
**# update-initramfs -a**
After installing this, the problem was solved!!

not true!
```
#update-initramfs -a
```
Illegal option -a

should be [B]# update-initramfs -u

[/B]otherwise this is misleading

there is more to do, however root access essentials are not mentioned here.;)

[solved]:-D

---

### Post by megabega on 2012-03-07
is it possible to show me step by step how to do this?

I do get de notification dev/disk/by-uuid/..... does not exist

pleas explain in baby steps i'm a noooooooob.

thanks

---

### Post by ScientificProp on 2012-03-08
This problem seems very similar to the situation I am having where I get the same boot error message root device not found after installing 11.10 onto a USB HDD from LiveUSB. I've tried various ideas to determine / fix the problem, but no success yet. I'm not sure how to try the suggested modification to add a command "update-initramfs -a" (or is it -u?), and I don't know where I'm supposed to add this command.

Thanks, ScientificProp

---

