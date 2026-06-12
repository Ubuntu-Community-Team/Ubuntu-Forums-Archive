---
title: "LVM Snapshot"
date: 2016-06-19
forum: Installation &amp; Upgrades
---

### Post by Pen16 on 2016-06-19
Okay so it has taken me much work to get to this point but I want a backup of my LVM partition so I can recover is anything happens. I have realized that I needed unallocated space left on the volume to create a logical volume snapshot so I booted into a live disk and resized my main partition to allow a 10G buffer as my snapshot is 6G. I then (I believe) I created a snapshot that is now sitting in my /dev/mapper/ directory. The file itself, like all the others, contains 0 bytes so I assuming it to be normal.  Now I am trying to mount the snapshot but it does not allow me to and when it does there are no contents in the mounted directory? mkdir /mnt/backup mount dev/mapper/ubuntu--vg-backup mnt/backup  Mount: unknown file system type "swap"  Then when I graphically navigate to the directory it is empty These are my logical volumes: Disk /dev/mapper/sda5_crypt: 55.4 GiB, 59496202240 bytes, 116203520 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes   Disk /dev/mapper/ubuntu--vg-root: 35 GiB, 37580963840 bytes, 73400320 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes   Disk /dev/mapper/ubuntu--vg-swap_1: 6 GiB, 6387924992 bytes, 12476416 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes   Disk /dev/mapper/ubuntu--vg-backup: 6 GiB, 6387924992 bytes, 12476416 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes   Disk /dev/mapper/cryptswap1: 6 GiB, 6387400704 bytes, 12475392 sectors Units: sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes  Did I snapshot the wrong one or what is it that I am doing wrong here? Any help is greatly appreciated.

---

### Post by Dennis N on 2016-06-19
> I want a backup of my LVM partition so I can recover is anything happens...

A snapshot won't do you any good for recovery purposes if the volume you took the snapshot of can't be read. The snapshot volume keeps a record of the original contents only if the original contents get changed. Nothing else is copied to the snapshot. For example, if sector #327 on the original volume is changed after you make the snapshot, the original contents of that sector are saved to the snapshot volume. If you later restore (merge) the snapshot, the original contents that were saved are copied back. The purpose of this is to reverse all changes made to the original volume after the snapshot is started. The parts of the original volume that never changed are only on the original - so if the original volume is corrupted they are lost.

You need to use a backup method to another location where all the files you want to backup get copied.

---

### Post by Pen16 on 2016-06-19
Thank you very much clarified some much needed information. Thank you

---

