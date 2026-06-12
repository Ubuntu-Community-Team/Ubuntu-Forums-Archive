---
title: "do-release-upgrade (16.04 to 18.04) grub-install failed"
date: 2021-07-19
forum: Installation &amp; Upgrades
---

### Post by itwerks on 2021-07-19
Hello all,

I've got an extremely hot issue, grub-install failed while executing an in-place upgrade of Ubuntu 16.04 to Ubuntu 18.04 and the system no longer boots.

System specs:
Lenovo TD340 w/ LSI MegaRAID Software Raid controller
OS drive = 1TB WD 7200 SATA drive in RAID0 [/boot partition, / partition, swap, MBR partition table]
Data drives = 2x 4TB Seagate drives in RAID1 [mounted as /mnt/md0, GPT partition table]

During initial setup years ago I found it impossible to get Ubuntu installed without adding the drives to the LSI controller.  I suspected this upgrade would go sideways and sure enough here we are.  I need to get this sytem running again ASAP.  Help!

When the system was running /boot and /root were mounted like so:

/dev/md126p1 == /boot
/dev/md126p2 == /
/dev/md126p3 == swap

When do-release-upgrade failed on grub-install I rebooted to a Ubuntu 20.04 live session, installed boot-repair and ran the Recommended repair option.  Repair completed without errors but after a reboot I no longer had a grub prompt at all and subsequent attempts have left me with "missing operating system".  I just generated a boot info summary, it is available here: [https://paste.ubuntu.com/p/8nsJcMb9Qp/](https://paste.ubuntu.com/p/8nsJcMb9Qp/)

I'm not sure how to proceed... the OS drive is mountable and all of the data is accessible via a live session.  I haven't tried to interact with the data array at all as I know it mounts fine when the system boots.  I really need to get this fixed ASAP and appreciate any guidance these forums can offer. 

Please *(please please)* advise...

J

---

### Post by itwerks on 2021-07-19
I've succeeded in booting the machine using a SuperGrub2 boot disk, however I am unable to install grub to any of the attached disks.

I've tried:
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
sudo grub-install /dev/sdc
sudo grub-install /dev/sdd
sudo grub-install /dev/sde (USB backup drive)
sudo grub-install /dev/md126p1
sudo grub-install /dev/md126

All attempts fail with the following error:
grub-install: error: disk `mduuid/hash,1' not found

ls -l /dev/disk/by-id shows the device it claims cannot be found is linked to /dev/md126p1.

---

