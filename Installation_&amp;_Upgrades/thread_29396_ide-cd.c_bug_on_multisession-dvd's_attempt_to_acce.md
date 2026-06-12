---
title: "ide-cd.c bug on multisession-dvd's: attempt to access beyond end of device"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by floogy on 2005-04-24
Hello everyone,

Sorry, this is a crosspost. Additional Information can be found here:[MOUNTING DVD: ide-cd.c bug on multisession: attempt to access beyond end of device](http://ubuntuforums.org/showthread.php?t=29506&highlight=dvd+ide-scsi) .
It might be better to discuss it there.

Is there a active usenet newsgroup for ubuntu?

I simply don't know where this post suits the best. Yes, I do have some problems with forums like this, where I often doesn't know where's the best place for what kind of Question.

I got the following error in the kern.log:

attempt to access beyond end of device
hdc: rw=0, want=18446744073707837316, limit=7533056

It's due to a bug in ide-cd.c of the kernel.
I use 2.6.11-1-amd64-k8.

Please read [http://lists.debian.org/cdwrite/2004/06/msg00086.html](http://lists.debian.org/cdwrite/2004/06/msg00086.html) and
[http://www.fifi.org/doc/dvd+rw-tools/#isofs4gb](http://www.fifi.org/doc/dvd+rw-tools/#isofs4gb) .

So I ***have*** to route my dvd device trough ide-scsi, to read my multisession backup-dvd, because the first session is bigger than 2,2 GiB. the second is >1,3GiB.

Unfortunately I don't know how to setup the ide-scsi emulation for that dvd-drive.

I followed this howto:
[http://ubuntuforums.org/showthread.php?t=27369&highlight=ide-scsi](http://ubuntuforums.org/showthread.php?t=27369&highlight=ide-scsi)
and got this kernel line:
Kernel command line: root=/dev/sda9 ro console=tty0 quiet splash hdc=ide-scsi

But the kernel failed to route hdc through ide-scsi.

There was an error message at boot time, but dmesg didn't capture it.
I have to edit: 
vi /etc/default/bootlogd.
 # Run bootlogd at startup ?
BOOTLOGD_ENABLE=Yes

And post more details later.

Update:
bootlog.d wasn't able to log that error either, so I had to write it down by hand:

modprobe -k ide-mod options "hdc=ide-scsi"
FATAL: module ide_mod not found!

I use s-ata for root. and there are no sdc? build in /dev by udev
 ls /dev/sd*
/dev/sda   /dev/sda10  /dev/sda2  /dev/sda5  /dev/sda7  /dev/sda9
/dev/sda1  /dev/sda11  /dev/sda3  /dev/sda6  /dev/sda8

And also hal and the gnome-volume-manager are mounting the dvd as /dev/hdc on /media/cdrom0 :
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=gerhard)

 lsmod |grep id
video                  18824  0
ide_scsi               17284  0
ide_generic             1792  0
ide_disk               18240  0
ide_cd                 44680  1
ide_core              148996  5 amd74xx,ide_scsi,ide_generic,ide_disk,ide_cd
cdrom                  43176  2 ide_cd,sr_mod
scsi_mod              153584  5 ide_scsi,sbp2,sr_mod,sd_mod,libata


So, I need to know how to setup routing an ATAPI device properly on Ubuntu Horay with 2.6.x kernels. What do I have to do for the kernel modules, udev.rules hal and the gnome-volume-manager are working properly with ide-scsi instead of the recommended, but in this case not working ide-cd ?

Kind regards

floogy

---

