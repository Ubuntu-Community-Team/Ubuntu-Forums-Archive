---
title: "Trusty Tahr BTRFS Multi Disk Installation"
date: 2015-03-17
forum: Installation &amp; Upgrades
---

### Post by nroclaed on 2015-03-17
Can the Trusty Tahr installer perform multi disk BTRFS installations?  /dev/sda will hold 1 partition formated as BTRFS and mounted as /.  Grub will be installed on /dev/sda using 10 GB unpartitioned space at the beginning of the disk.  Swap will mount on a mdadm RAID1 array somewhere else.  Ultimately, /dev/sdb and /dev/sdc will each hold 2 partitions configured as BTRFS RAID 0 and RAID 1 devices mounted as  /exports and /svr respectively.  Can I accomplish this from within the installer?  If not, should I limit my use of the installer to pre-partition /dev/sdb and /dev/sdc or can I also configure the file systems as BTRFS and mount /exports and /svr as not RAID arrays on ,say, /dev/sdb?  In this scenario, the RAID conversion would be a post installation procedure.

Does the answer change if I add a separate ext2 partition to /dev/sda to mount /boot?

---

### Post by Skaperen on 2015-03-17
i use BTRFS but i keep the **system** in **separate** partitions as i have done since ye old mainframe days

---

