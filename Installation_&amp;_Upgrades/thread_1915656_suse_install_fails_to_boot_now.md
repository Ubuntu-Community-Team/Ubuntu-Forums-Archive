---
title: "suse install fails to boot now"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2012-01-26
I have a multi boot box with grub2 installed on the mbr of /dev/sdc. Ubuntu and suse are on /dev/sdc. Win XP is installed on /dev/sdd. The drives /dev/sda and /dev/sdb are data drives.

When I installed suse12.1, I went in to ubuntu and did a gurb update and I have been able to boot into suse. There is an issue that when I boot into suse, I get the following,

resume device not found (ignoring)
waiting for device /dev/sdc3 to appear
want me to fall back to /dev/disk/by-id/ata-WDC...... (Y/n)

When I enter Y, suse will boot. Why there seems to be an issue finding the drive is unclear to me.

Today, it will not boot into suse when I enter Y. A while ago I had a problem and moved my hard drives to a PCI sata controller card. When I did that, I was not able to boot into anything any more. I used [[COLOR="Blue"]_boot-repair_[/COLOR]]("https://help.ubuntu.com/community/Boot-Repair") and was able to boot back into windows and ubuntu. I didn't try suse at the time, so I don't know if this problem is a hold over from the problem I repaired with boot-repair or not.

I have attached the results file from the boot_info script. The script seems to indicate that I have grub installed on the mbr of the windows drive as well as sdc. I am surprised at this because I am sure I removed all copies of grub except the on I installed with ubuntu.

Any suggestions on how to get back into suse?

**[COLOR="Navy"]LMHmedchem[/COLOR]**

---

### Post by LMHmedchem on 2012-01-26
Is this likely an issue of suse not having the drivers for the PCI card that the drive is plugged into? I really need sues right now (or course), so I need to be able to solve this. Maybe I can get in with super grub 2, but I'm not sure that grub is the issue.

LMHmedchem

---

