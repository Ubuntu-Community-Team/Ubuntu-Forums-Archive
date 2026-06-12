---
title: "md devices and hibernation"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chrroessner on 2008-09-12
Hi,

I am not sure, if this is a _bug_, so I ask here in the forum. Hopefully some developers are reading this, too.

I use this md-configuration:

```

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c96cab68:2c4fdfbd:799f5a3b:588da548
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=060f6c67:d95830c9:799f5a3b:588da548

```

md1 holds a lvm setup:

```

pvdisplay 
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               vg01
  PV Size               465,66 GB / not usable 163,44 MB
  Allocatable           yes 
  PE Size (KByte)       524288
  Total PE              931
  Free PE               212
  Allocated PE          719
  PV UUID               s1FFx3-GF2b-1AB5-Td0H-Q7fU-LDZb-RGgC3y

```

And this is my current mount table:

```

/dev/mapper/vg01-lv_root on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-3-generic/volatile type tmpfs (rw,mode=755)
/dev/md0 on /boot type ext3 (rw,relatime)
/dev/mapper/vg01-lv_p1 on /home type ext3 (rw,relatime)
/dev/mapper/vg01-lv_p2 on /media/lv_p2 type ext3 (rw,relatime)
/dev/sdb1 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/croessner/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=croessner)

```

So far so good. I checked suspend and hibernation and was really, really happy, because it works so fine since I am waiting for this for years.

When I tested hibernation, I could see the following:

After powering on the machine again, first the kernel started booting, reading the initramfs and there was a notice that md1 was not cleanly shut down and that the raid would be repaired in background. A few seconds later the resume process started and after entering my password, I just opened a terminal to see, if there was goining on something with md1:

```

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdc5[0] sda5[1]
      488279488 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[0] sda1[1]
      104320 blocks [2/2] [UU]
      
unused devices: <none>

```

So now the only question is: Could be the hibernation a problem for my raid devices? Is this a normal behaviour or should this be reported as a critical bug? What was, if the background process had started? Would this destroy all my data?

Thanks for your answers.

Christian

---

