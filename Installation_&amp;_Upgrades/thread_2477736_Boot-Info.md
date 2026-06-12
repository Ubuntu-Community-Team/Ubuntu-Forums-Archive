---
title: "Boot-Info"
date: 2022-08-05
forum: Installation &amp; Upgrades
---

### Post by wmstrome on 2022-08-05
Boot-Repair suggests posting the Boot-Info report before attempting to do the repair.  My report is at:
[https://paste.ubuntu.com/p/wRJKMyWjn3/](https://paste.ubuntu.com/p/wRJKMyWjn3/)
in summary,
OS#1:   Ubuntu 15.10 on sdb3  --- no longer use
OS#2:   Linux Lite 5.0 (20.04) on sdb7 -- no longer use
OS#3:   Ubuntu 22.04.1 LTS on sdc6 -- This is the one I use and want to repair
OS#4:   Windows 7 on sdc3 -- no longer use

There really is no Windows installation. The partition was from a long time ago (/dev/sdc3).  Ubuntu 15.10 on sdb3 is no longer used. Also, the Linux-Lite installation on /dev/sdb7 is corrupt so don't use it either.  Should I use gparted to delete or reformat those partitions before I do the default boot repair? The boot became corrupt after I had been working with a Live USB of XUbuntu to try to solve an Ethernet connection problem.

Thanks for any help.

---

### Post by oldfred on 2022-08-05
You did not post or overwrote the Boot-Repair summary report with your comments.

I have multiple old Ubuntu installs, and just turn off os-prober. I then only add boot stanzas that I want into 40_custom.
You can delete old installs or turn off os-prober.

You may need to run advanced options to choose correct install for Boot-Repair to fix. 
Make sure you are in correct boot mode, either UEFI or BIOS to match how you installed.

---

### Post by wmstrome on 2022-08-05
Thanks for your quick reply. Is there an easy way to determine which boot mode I used when I installed it? It is so long ago that I don't remember.  I have decided to remove the old installations and run boot-info again to see what it says.  I can make better use of the disk space than just holding obsolete installations.

---

### Post by oldfred on 2022-08-05
Better to see report.
New installs now seem to always add an ESP - esp system partition which for BIOS the ESP is not needed (now) and UEFI installs where ESP is required.
They may be doing that to make it easier to update to UEFI install as UEFI has been the standard for 10 years.
BIOS is for older hardware or just some users who still want to use BIOS boot mode.

Still better to use gpt partitioning whether BIOS or UEFI, but with gpt you need a bios_grub partition for BIOS boot or an ESP for UEFI boot.

---

