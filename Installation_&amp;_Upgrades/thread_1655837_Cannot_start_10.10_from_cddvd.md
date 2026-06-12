---
title: "Cannot start 10.10 from cd/dvd"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Parmax on 2010-12-30
:confused: Hi there. It's my first time trying to use Ubuntu and obviusly I've done smoething wrong. I've followed the instructions about burning the iso file but when my PC boots from the dvd for trial mode there is a message:

(initramfs) Can not mount/dev/loop0 
(cdrom/casper/filesystem.squqshfs) on //filesystem.squashfs

does anybody know what it means?

---

### Post by coffeecat on 2010-12-30
Error messages like that are often due to a bad or misread disc. When you say you followed the instructions for burning, did you check the md5sum of the downloaded ISO and did you burn at a slow speed?

---

### Post by IWantFroyo on 2010-12-30
Maximum speed for burning ISO's is about 16x. Any more and it won't work. But about the error. 
To get to Ubuntu you might have to turn off acpi. Go into Grub and type acpi=off. Then boot.
If this works, put this in command prompt without quotes:
gksudo gedit /etc/default/grub
find the line: GRUB_CMDLINE_LINUX=""
Change it to: GRUB_CMDLINE_LINUX="noapic acpi=off"

---

