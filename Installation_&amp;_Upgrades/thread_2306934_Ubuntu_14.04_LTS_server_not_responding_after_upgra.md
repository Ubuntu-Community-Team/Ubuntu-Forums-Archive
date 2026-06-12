---
title: "Ubuntu 14.04 LTS server not responding after upgrade from 12.04 LTS"
date: 2015-12-20
forum: Installation &amp; Upgrades
---

### Post by GZW on 2015-12-20
Hi folks,

today I did
```
sudo do-release-upgrade
```
on my remote server which was running Ubuntu 12.04 LTS.

As I am not an expert with Unix, maybe that was not a good idea.

The upgrade did take place and I was asked to reboot. I said 'yes'.  After that I was not able to connect via SSH any more...

As far as I understand, GRUB is not properly configured. Here is some information I took when the upgrade was processing:
```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
File descriptor 54 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 55 (/dev/pts/0) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 56 (/dev/pts/0) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 99 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 145 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 149 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 150 (/dev/pts/0) leaked on lvs invocation. Parent PID 20883: /bin/sh
File descriptor 151 (/dev/pts/0) leaked on lvs invocation. Parent PID 20883: /bin/sh
  No volume groups found
Found Ubuntu 12.04.4 LTS (12.04) on /dev/sda3
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
done
Removing linux-image-3.2.0-77-generic (3.2.0-77.114) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-77-generic /boot/vmlinuz-3.2.0-77-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
File descriptor 54 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 55 (/dev/pts/0) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 56 (/dev/pts/0) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 99 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 145 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 149 (/var/log/dist-upgrade/apt.log) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 150 (/dev/pts/0) leaked on lvs invocation. Parent PID 23056: /bin/sh
File descriptor 151 (/dev/pts/0) leaked on lvs invocation. Parent PID 23056: /bin/sh
  No volume groups found
Found Ubuntu 12.04.4 LTS (12.04) on /dev/sda3
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
/usr/sbin/grub-probe: warning: Couldn't find physical volume `(null)'. Some modules may be missing from core image..
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

```


As of now, I am able to start a Rescue system (thanks to Hetzner).
But I don't know how to fix the issue.

An overview over partitions:
```

root@rescue ~ # parted -l
Model: ATA SAMSUNG HD403LJ (scsi)
Disk /dev/sda: 400GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  2147MB  2146MB  primary  linux-swap(v1)  raid
 2      2147MB  2684MB  537MB   primary  ext3            raid
 3      2684MB  400GB   397GB   primary  ext4            raid




Model: ATA SAMSUNG HD403LJ (scsi)
Disk /dev/sdb: 400GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  2147MB  2146MB  primary  linux-swap(v1)  raid
 2      2147MB  2684MB  537MB   primary  ext3            raid
 3      2684MB  400GB   397GB   primary  ext4            raid




Model: Linux Software RAID Array (md)
Disk /dev/md0: 2146MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  2146MB  2146MB  linux-swap(v1)




Model: Linux Software RAID Array (md)
Disk /dev/md1: 537MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  537MB  537MB  ext3




Model: Linux Software RAID Array (md)
Disk /dev/md2: 397GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  397GB  397GB  ext4

```

Can anyone please guide me what I need to do in order to fix GRUB? Thank you very much!

---

### Post by GZW on 2015-12-21
I took me about 10 hours, but finally this solved it for me:

```

mount /dev/md2 /mnt
mount /dev/md1 /mnt/boot
grub-install --root-directory=/mnt /dev/sda

```

---

