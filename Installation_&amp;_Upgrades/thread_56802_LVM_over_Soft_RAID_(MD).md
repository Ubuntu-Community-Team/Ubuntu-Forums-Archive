---
title: "LVM over Soft RAID (MD)"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by dainok on 2005-08-14
Hi all, I'm new to Ubuntu but not to Linux World.
If you want to intall Ubuntu in a LVM+MD configuration please pay attention: before reboot first time edit **/etc/udev/links.conf** and add md device you've configured.
Edit **/etc/lvm/lvm.conf** also and set **md_component_detection = 1**

For example:
My system have 4 md device:
/dev/md0 with reiserfs for / filesystem
/dev/md1 for swap
/dev/md2 with LVM for /home, /opt, /tmp, /usr, /var
/dev/md3 with LVM for data

So I've added in /etc/udev/link.conf:
M md0           b 9 0
M md1           b 9 1
M md2           b 9 2
M md3           b 9 3

If you don't add this lines, RAID can't detect other md device exept md0, and LVM start before RAID. In this case you don't have a RAID device (mirror raid in my case), and LVM see "duplicated PV" (the exact error is: "Found duplicated PV ...:using /dev/...") and kernel upgrade can't go right.

---

