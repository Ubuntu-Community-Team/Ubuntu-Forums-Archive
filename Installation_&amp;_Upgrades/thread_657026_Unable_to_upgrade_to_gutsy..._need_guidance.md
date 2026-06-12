---
title: "Unable to upgrade to gutsy... need guidance"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by tiger.woods on 2008-01-03
I get the message "not enough disk space" when trying to upgrade to gutsy. My /boot partition has 66meg free, how much does it need for the upgrade? Does it really need more?

I've gone through the /boot partition and all that is there is the current kernel and a copy .bak that is only 6.6meg in size and some other significant files needed, nothing else to delete.

What are my options?

Thanks,

---

### Post by Borbus on 2008-01-03
Did you actually set that partition as /boot in the partitioner and not /?

---

### Post by tiger.woods on 2008-01-03
Since this is an upgrade I'm not able to select the partition? so I'm not sure how to answer your question.

TW,

---

### Post by PmDematagoda on 2008-01-03
Do you have enough free space for the root of Ubuntu?

---

### Post by sciencewhiz on 2008-01-03
post the results of df -h and fdisk -l

---

### Post by tiger.woods on 2008-01-03
Can do, I'll post back a little later since I'm now at the office.

Thanks,

---

### Post by tiger.woods on 2008-01-03
As requested her is the output of df -h and fdisk -l.

root@dns1:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              12G  6.1G  4.4G  59% /
varrun                252M  116K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   92K  252M   1% /proc/bus/usb
udev                  252M   92K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/hda1              89M   21M   63M  25% /boot
/dev/hda5             176G  7.1G  160G   5% /video


root@dns1:~# fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          12       96358+  83  Linux
/dev/hda2              13          74      498015   82  Linux swap / Solaris
/dev/hda3              75        1533    11719417+  83  Linux
/dev/hda4            1534       24792   186827917+   5  Extended
/dev/hda5            1534       24792   186827886   83  Linux

---

### Post by tiger.woods on 2008-01-04
I managed to strip out a few more files from the /boot directory to allow for the upgrade.

---

