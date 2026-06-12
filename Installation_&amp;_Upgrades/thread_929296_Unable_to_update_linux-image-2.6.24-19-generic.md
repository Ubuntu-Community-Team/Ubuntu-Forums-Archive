---
title: "Unable to update linux-image-2.6.24-19-generic"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by burdettn on 2008-09-24
Hi,
   I am new to ubuntuI've installed Hardy and clicked on the red down arrow which launches the update manager. Everything seems to install (121 packages) except for linux-image-2.6.24-19-generic. The error I get is;

Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.34 (using .../linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.24-19-generic/kernel/net/lapb/lapb.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.

So I assume I don't have enough diskspace! But doing a "df -k" gives the following.

Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sda5               233335    184336     36551  84% /
varrun                 1036868       116   1036752   1% /var/run
varlock                1036868         0   1036868   0% /var/lock
udev                   1036868        80   1036788   1% /dev
devshm                 1036868        12   1036856   1% /dev/shm
/dev/sda1                60185     22735     34239  40% /boot
/dev/sda7            230117076  80307520 138120264  37% /home
/dev/sda9               988084     17732    920556   2% /tmp
/dev/sda8              6008656   1811440   3894396  32% /usr
/dev/sda10             1976236    443852   1432784  24% /var
tmpfs                  1036868     39760    997108   4% /lib/modules/2.6.24-19-generic/volatile

Looks like I have enough space?

uname -a => Linux duodenum-sl 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

cat /etc/lsb-release => 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

I can't see any old distributions of the linux kernel on the system

dpkg -l | grep linux-image =>
ii  linux-image-2.6.24-19-generic              2.6.24-19.34                             Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.19.21                             Generic Linux kernel image

Any ideas? I'm completely stuck

Cheers
Neil

---

