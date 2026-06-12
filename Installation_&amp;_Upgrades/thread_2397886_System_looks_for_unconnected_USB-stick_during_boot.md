---
title: "System looks for unconnected USB-stick during boot"
date: 2018-08-04
forum: Installation &amp; Upgrades
---

### Post by alexb888 on 2018-08-04
I installed Ubuntu 18.04 on the laptop using mini.iso written to USB-stick. Previouslyon this laptop Ubuntu 16.04 was installed, so existing partitions, including swap, were used, they just was wiped and reformatted. Installation went fine, but after that I noticed that system "hangs" for a while during boot process. Although systemd-analyze reports that everything is ok


```
$ systemd-analyze 
Startup finished in 2.312s (kernel) + 1.961s (userspace) = 4.273s
graphical.target reached after 1.955s in userspace

```

I have checked dmesg and could not find anything suspicious. But in the journal there are some strange lines


```
$ journalctl --system
...
Aug 04 14:35:50 laptop kernel: scsi 6:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 4
Aug 04 14:35:50 laptop kernel: sd 6:0:0:0: Attached scsi generic sg1 type 0
...
Aug 04 14:35:51 laptop kernel: sd 6:0:0:0: [sdb] 15124992 512-byte logical blocks: (7.74 GB/7.21 GiB)
Aug 04 14:35:51 laptop kernel: sd 6:0:0:0: [sdb] Write Protect is off
Aug 04 14:35:51 laptop kernel: sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Aug 04 14:35:51 laptop kernel: sd 6:0:0:0: [sdb] No Caching mode page found
Aug 04 14:35:51 laptop kernel: sd 6:0:0:0: [sdb] Assuming drive cache: write through
...

```
The "USB DISK 2.0" mentioned here is the same USB-stick which was used during installation process. But it was not connected to the laptop during boot and no other devices were connected. I checked /etc/fstab but it contains only partitions from SSD and there are not sign of the any removable device in it.


I tried to reboot laptop several times, and every time system "hangs" and same messages mentioning "USB DISK 2.0" appear.


Any ideas what happening here and how to fix it?

---

### Post by oldfred on 2018-08-04
Do UUIDs of swap match? Sometimes a reinstall changes UUID.
cat /etc/fstab
lsblk -f

---

### Post by alexb888 on 2018-08-04
Yes, all UUIDs match.

---

