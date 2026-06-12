---
title: "switching from Ubuntu 32 to Kubuntu 64 bit"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2006-12-09
I've been running Ubuntu Dapper/Edgy 32 bit version on my 64 bit system for a while and want to try out Kubuntu (64 bit). I have the DVD version of Kubuntu burned, though I can't remember if it was a normal or alternative version, or if there is a difference with the DVD ISOs.

Anyhow, I tried to boot from the DVD and install this morning, but panicked a little at the partitioning stage. I have three hard drives installed - hda, hdb and sda. Sda is the main drive and contains the OS and my home. I want to format just the system part of the disk and leave /home intact. At the installation stage, the installer/partitioner doesn't seem to want to give me the option. It looks as though it only recognises sda as one disk and will format all or nothing. 
Considering the output from the **mount** command below, do I in fact have no partitioning on the disk sda and am I doomed to losing all information on /home if I perform a fresh install of Kubuntu now? I can't figure out how this happened as on my previous installation of Ubuntu, on the disk hda, I had separate partitions for / and /home (hda6 and hda7)

To sum up
1) how do I know if I have the right installation media?
2) what options (if any) can I use to avoid losing all data on /home and still wipe the system files?


```

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
/dev/hda6 on /media/oldhome type ext3 (rw,errors=remount-ro)
/dev/hda7 on /media/oldsystem type ext3 (rw,errors=remount-ro)
/dev/hdb1 on /media/supersize type ext3 (rw,errors=remount-ro)
/dev/hdb5 on /media/games type ext3 (rw,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

