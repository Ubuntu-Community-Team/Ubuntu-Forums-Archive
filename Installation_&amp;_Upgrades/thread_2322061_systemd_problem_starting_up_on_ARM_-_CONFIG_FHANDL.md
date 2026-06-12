---
title: "systemd problem starting up on ARM - CONFIG_FHANDLE not set in kernel"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by phil-dialsolutions on 2016-04-26
I've just updated from 14.04 to 16.04 on my banana pi, but while booting, systemd reports itself as waiting for four devices
sda1
sda2
ttyS0
eth0

sda1 is my swap partition
sda2 is an ext4 partition for storage not related to the boot process

If I give a root password to log in to emergency mode, mount /dev/sda2, swapon -a and then init 2, I get a working system.

From what I've read, in order to work with systemd version >=209 the kernel should have CONFIG_FHANDLE enabled but /proc/config.gz shows
#CONFIG_FHANDLE is not set

uname -a gives
Linux mail 3.4.90 #2 SMP PREEMPT Tue Aug 5 14:11:40 CST 2014 armv7l armv7l armv7l GNU/Linux

If my understanding is correct, the released kernel should be built with CONFIG_FHANDLE enabled.

Can anyone tell me if I've misunderstood what's going wrong or whether I should file a bug report?

Thanks

Phil

---

### Post by phil-dialsolutions on 2016-04-26
I note that kernel config for the 4.4.0-21-lowlatency kernel I'm using on 16.04 on my laptop, has CONFIG_FHANDLE=y

---

### Post by ajgreeny on 2016-04-26
Can we see the output of terminal command ```
sudo blkid -c /dev/null
``` after you have got the system running properly followed by the output of ```
cat /etc/fstab
``` both in [code tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168") please.

---

### Post by phil-dialsolutions on 2016-04-26
```

blkid -c /dev/null
/dev/sda1: UUID="f5c75bc5-1364-4e17-aa14-d34cfac8f42d" TYPE="swap" PARTUUID="000b1ce1-01"
/dev/sda2: UUID="e5859619-cd70-4aa8-aa83-1ac32436091a" TYPE="ext4" PARTUUID="000b1ce1-02"
/dev/mmcblk0: PTUUID="0001df35" PTTYPE="dos"
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="324A-3901" TYPE="vfat" PARTUUID="0001df35-01"
/dev/mmcblk0p2: UUID="61187ff0-d686-48dd-832e-f8f0589696e9" TYPE="ext4" PARTUUID="0001df35-02"

```

```

cat /etc/fstab 
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/dev/sda2 /mnt/harddisk               ext4    errors=remount-ro 0       1
/dev/sda1 none                        swap    sw                0       0

```

---

### Post by ajgreeny on 2016-04-26
Your problem seems to be that fstab makes no mention of the root partition but has entries only for the data partition sda2 and swap. It points this out in the comment ```
# UNCONFIGURED FSTAB FOR BASE SYSTEM
```

Let's see the output now from ```
sudo parted -l
``` to see what partitions you really have on that machine and figure out if we can add an entry for the root partition.

PS:
I don't know banana pi at all nor any of the other pi devices, but I assume that the filesystem for a *ubuntu OS on them is similar to, if not identical to, that on a standard PC.

---

### Post by phil-dialsolutions on 2016-04-26
Thanks for your help with this!
```

parted -l
Model: ATA WDC WD20NPVX-00E (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  1075MB  1074MB  primary  linux-swap(v1)
 2      1075MB  2000GB  1999GB  primary  ext4




Model: SD SD8GB (sd/mmc)
Disk /dev/mmcblk0: 7969MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  64.0MB  62.9MB  primary  fat16
 2      64.0MB  7969MB  7905MB  primary  ext4

```

It bears mention that this machine has been running on Ubuntu 14.04 for over a year, and if fstab has changed, it's as a result of the upgrade process to 16.04 - I haven't manually edited it since initial installation a year ago, when I added the partitions on /dev/sda.

The output of mount may be of interest, as the root filesystem is mounted and accessible, and I haven't had to manually mount it.

```

mount
/dev/mmcblk0p2 on / type ext4 (rw,relatime,data=ordered)
devtmpfs on /dev type devtmpfs (rw,relatime,size=447604k,nr_inodes=111901,mode=755)
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,nodev,mode=755)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,relatime,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpuacct,cpu)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
sunrpc on /run/rpc_pipefs type rpc_pipefs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
nfsd on /proc/fs/nfsd type nfsd (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda2 on /mnt/harddisk type ext4 (rw,relatime,errors=remount-ro,data=ordered)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/0 type tmpfs (rw,nosuid,nodev,relatime,size=89544k,mode=700)



```

---

### Post by phil-dialsolutions on 2016-04-26
The banana pi boots from a FAT partition on the SDCARD (/dev/mmcblk0p1). Boot configuration seems to be controlled by the uEnv.txt file. Perhaps this is how the root partition is mounted rather than an entry in fstab?

```

cat uEnv.txt 
aload_script=fatload $device $partition 0x43000000 /script.bin;
aload_kernel=fatload $device $partition 0x48000000 /uImage;bootm 0x48000000
uenvcmd=run aload_script aload_kernel
bootargs=console=ttyS0,115200 console=tty0 disp.screen0_output_mode=EDID:1280x720p60 hdmi.audio=EDID:0 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait

```

---

### Post by ajgreeny on 2016-04-26
OK, I see root is this partition
```
/dev/mmcblk0p2 on / type ext4 (rw,relatime,data=ordered)
```
so maybe we need to add the following to fstab to see if you can then boot direct into the OS without the lag or pause.
```
# / was on /devmmcblk0p2/ during installation
UUID=61187ff0-d686-48dd-832e-f8f0589696e9 /               ext4    errors=remount-ro 0       1
```though you may wish to try using the same options (rw,relatime,data=ordered) as shown in your own mount output rather than those I have shown which are from my own desktop fstab; perhaps your pi's options need to be different.

Edit and save the fstab file (after backing it up in case all goes to worms) and then run the command ```
sudo mount -a
``` as a test of the syntax and to check for any errors.

If none of this works I am afraid I do not think I can help you further.  Pis are something that I have no experience of at all.

---

### Post by phil-dialsolutions on 2016-04-26
Unfortunately I still get the minute and a half delay on the same four devices, and when the machine becomes up, /dev/sda2 is not mounted and swap is not available.

[COLOR=#000000]I'm leaning towards my initial suspicion that this is a systemd problem caused by CONFIG_FHANDLE not being enabled in the kernel config, but yesterday was the first time I've ever used systemd, so I'm on a steep learning curve!

[/COLOR]Thank you very much for your help!

---

### Post by ajgreeny on 2016-04-26
> **phil-dialsolutions said:**
> Unfortunately I still get the minute and a half delay on the same four devices, and when the machine becomes up, /dev/sda2 is not mounted and swap is not available.

[COLOR=#000000]I'm leaning towards my initial suspicion that this is a systemd problem caused by CONFIG_FHANDLE not being enabled in the kernel config, but yesterday was the first time I've ever used systemd, so I'm on a steep learning curve!

[/COLOR]Thank you very much for your help!
I think many users are on the same steep learning curve as you.

Sorry I can't help, but I'll keep an eye on the thread to see if it is solved for you by someone more knowledgable than me.

---

### Post by phil-dialsolutions on 2016-04-28
Update: It turns out that the kernel I'm running isn't the one supplied with 16.04. The nature of the boot sequence on the banana pi (uboot) is that it seems to be running a kernel from the uImage file on the boot partition of the sdram card. That kernel doesn't have [COLOR=#000000]*CONFIG_FHANDLE enabled so may be responsible for the systemd timeouts on boot. However I notice that the armhf kernel for 16.04 doesn't have *[/COLOR][COLOR=#000000]*CONFIG_FHANDLE enabled either, so I may still have the problem once I've worked out how to get the machine to run off the Ubuntu 16.04 kernel. Thanks again to ajgreeny for your help on this.*[/COLOR]

---

