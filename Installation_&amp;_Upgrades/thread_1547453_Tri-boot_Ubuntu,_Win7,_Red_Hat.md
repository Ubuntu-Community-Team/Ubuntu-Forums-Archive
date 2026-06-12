---
title: "Tri-boot Ubuntu, Win7, Red Hat"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by TJEnger on 2010-08-06
I have Windows 7 and Ubuntu 10.04 on sda. Currently GRUB 2 v1.98 is on sda MBR and boots either operating system properly.
 
I'd like to install Red Hat on sdb, but don't know what to expect regarding booting it once it's installed. Should I select GRUB (MBR or sdb1), LILO, or none during the Red Hat installation? I assume I can add the Red Hat disk to existing GRUB on sda, but not sure how???
 
Ideas? Thanks in advance!

---

### Post by snowpine on 2010-08-06
Both options are viable. You can install Red Hat GRUB to /dev/sdb and choose between the drives each time you boot using your BIOS boot menu. Or, you can install Red Hat GRUB to /dev/sdb1 and chainload it from Ubuntu's GRUB on /dev/sda.

Red Hat support will fill you in on the details; that's what you're paying them for right? :)

---

