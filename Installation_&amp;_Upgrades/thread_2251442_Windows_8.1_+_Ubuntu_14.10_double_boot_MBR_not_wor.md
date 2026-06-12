---
title: "Windows 8.1 + Ubuntu 14.10 double boot MBR not working"
date: 2014-11-04
forum: Installation &amp; Upgrades
---

### Post by sduverge on 2014-11-04
Hello,
I have an Acer Aspire One D-150, with windows 8.1 installed and did a disk reduction and then created the new partition to install Ubuntu on it. All went well with the installation, except for the fact that I can't boot into windows anymore. I need it for work, so I can't wipe it out of my HDD.

I have syslinux installed and if I browse the folders I can find the /usr/lib/syslinux/mbr.bin file, however, when I run the command:
```
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
I get:
```
dd: failed to open ‘/usr/lib/syslinux/mbr.bin’: No such file or directory
```

I can access the windows partition and browse through the files, so I know I have a healthy partition and the files are safe.

Any ideas? Help?):P

---

### Post by ajgreeny on 2014-11-04
How did you shrink the Win8 partition?
How did you install Ubuntu? You must boot the USB or DVD in UEFI mode as I am pretty certain Win8 will be UEFI, and therefore Ubuntu also must be to get a successful dual booting system.

Boot-Repair in my signature will probably be the easiest way for us to see what you have at present on the computer, and it may be as simple as running that to restore a dual boot system for you, but don't blindly use the default repair; firstly show us the link to the report that Boot-Repair gives you.

---

### Post by arashiko28 on 2014-11-06
Hi, I'm sduverge, I just recovered my old ID.

There's a pretty easy process to shrink the partition in windows 8, you do it through disk manager, choose the partition and shrink it, it won't allow you to shrink at will, but what windows considers is good enough, in my case, it gave me 40GB.
I installed by booting from my USB and it was a pretty normal process.

I fixed it by accidentally choosing windows 8 to boot and allowing it to run the forced update installation, apparently the fact that it was pending, kept it from booting normally, after approximately 40 minutes, it booted normally into windows 8. (Before, It would try and then reboot and boot into Ubuntu).

---

