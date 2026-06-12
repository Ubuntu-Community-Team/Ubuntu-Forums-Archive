---
title: "system **vanished** after new HDD installed"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by nss0000 on 2010-04-09
Gents:

Running solo Ubuntu 9.1 on current AMD-965/MSI_gd70 desktop.

Recently I upgraded hardware ( new ram/2nd hdd/temp-probe ) on this kit. All function appeared nominal and all hardware appeared in BIOS. 

 After adding a new line in /etc/fstab to conjure-up my new 650-G sata I rebooted ... I can access **nothing** on my system  ... except FireFox and THAT because I have a FF_icon on my desktop.

 The system boots, and std Gnome GUI appears, but excepting *LOGIN* none of the tool-bars have any function whatsoever. I cannot reach the command-line ... whatever that might be worth. I appreciate any insight into this vanishing system issue.

---

### Post by nss0000 on 2010-04-09
A couple random re-boots ... and the system starts working again. 

Sure I feel stupid ... but I still do not know what happened when I listed HDD#2 in /etc/fstab.

---

### Post by nss0000 on 2010-04-09
> **nss0000 said:**
> A couple random re-boots ... and the system starts working again. 

Sure I feel stupid ... but I still do not know what happened when I listed HDD#2 in /etc/fstab.
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6c81e29c-2eba-42c4-a940-630b2c7c5fc8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7aaf326a-cc3a-4aa7-900f-95981847fffa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /mnt/sdb1 ext3 defaults 0 0

---

