---
title: "Kernel panic - can't even boot in recovery mode or live cd"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by gtmarley on 2008-01-27
I still had a NTFS partition and I finally copied all of my data to an ext3 partition.  Then I used gparted to reformat the old partition to ext3.  That all worked but the machine hung after I clicked the Close button on gparted to reload the partition tables.  I did a hard reboot but now my system hangs on boot.  I've tried recovery mode but it dies too.  I've also tried the live CD - still no boot.  I don't have another OS to dual boot to anymore.

Before this I've been running Gutsy 64-bit fine for a few months.  I did get system hangs once in a while usually while accessing the NTFS partition.  That's why I decided to retire it.

In recovery mode boot I get:
```

HARDWARE ERROR
CPU 0: Machine Check Exception:   4 Bank 4: b200000000070f0f
TSC 139fdedb190
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check

```

I'm a n00b, so I'm not adept at reading this stuff.

I also tried booting from a minimal cd and the system hung while "Detecting disks and all other hardware".  I haven't added any new hardware since first installing Gutsy in October.

My system:
ASUS A8N-E
Athlon 64 @ 2.0GHz
2 GB RAM
nVidia GeForce 2 MX/MX 400
4 SATA drives
Seagate 250 GB - sdc1 swap; sdc2 ext3 not mounted by default
Maxtor 250 GB - sdd1 was ntfs; now presumably ext3; **I suspect this drive**
Maxtor 250 GB - sda1 ext3 mounted as /
Western Digital 500GB - sdb1 ext3 mounted as /home

I'm going to try removing the suspect hd and see what happens.  I don't think there is a problem with the CPU as the boot info seems to suggest.  I don't know what mcelog is, so I'm grasping at straws. :confused:  I've got my work laptop (Win XP) at home for the weekend so I can do research with it.

Thanks in advance for any help you can offer.

---

### Post by Pumalite on 2008-01-27
Try:
no apic nolapic acpi=off
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by gtmarley on 2008-01-27
Thanks Pumalite.
Same result though.

---

### Post by Pumalite on 2008-01-27
Try the Alternate CD.Download iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Do md5sum on iso, burn as image at 4x or less.
Use good quality CD-R media.
Try again.

---

### Post by gtmarley on 2008-01-27
Thanks again.

I have disconnected the drive I suspected and now Gutsy boots!  I'm curious as to how the drive could cause such a fatal problem.

---

### Post by Pumalite on 2008-01-27
[http://ubuntuforums.org/showthread.php?p=3913531](http://ubuntuforums.org/showthread.php?p=3913531)

---

