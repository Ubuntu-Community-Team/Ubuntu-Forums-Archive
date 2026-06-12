---
title: "Unable to get past boot"
date: 2017-10-07
forum: Installation &amp; Upgrades
---

### Post by raiza2201 on 2017-10-07
Hello, i've been unsuccesfully trying to boot Lubuntu 17.04 to my laptop running Windows 10. Everytime i have the usb stick in and turn on my computer, it stops before booting and restarts to a never ending loop. I installed Ubuntu 16.04 on the same laptop months before without issues but had to delete it due to memory and space issues. I believe that it has to do with the GRUB booting since i deleted Ubuntu directly from the partition before uninstalling GRUB and had to manually uninstall it from the cmd. I already have my data backed up and want to do a clean install, replacing Windows completely so i don't mind losing any files on my pc. Hope someone can help me.

System Specs
Lenovo Yoga Ideapad
Intel Pentium CPU 2129Y 1.10GHz
4GB RAM
x64
Windows 10

---

### Post by mörgæs on 2017-10-09
Hi, welcome to the fora.

Does the USB stick work if you try it in another computer?

---

### Post by oldfred on 2017-10-09
What model Yoga?
And have you updated UEFI from Lenovo.

Some Yoga were part of a big flap from Linux & Lenovo as it did not have the AHCI mode.
supposedly fixed with updates.

 [https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments](https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments)
Lenovo Linux support - many obsolete versions of Linux
[https://support.lenovo.com/us/en/documents/pd031426](https://support.lenovo.com/us/en/documents/pd031426)
 Warning: Microsoft Signature PC program now requires that you can't run Linux. Lenovo Yoga 900 ISK2 UltraBook Sept 2016
[https://ubuntuforums.org/showthread.php?t=2337719](https://ubuntuforums.org/showthread.php?t=2337719)
[http://mjg59.dreamwidth.org/44694.html](http://mjg59.dreamwidth.org/44694.html)
[https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports#comments](https://hardware.slashdot.org/story/16/09/21/1516230/microsoft-signature-pc-requirements-now-blocks-linux-installation-reports#comments)
The 13" Lenovo 710S-13ISK is also affected by this. Not providing an AHCI mode makes sure:
- you can't run Linux on it
- you can't use the Gentoo based System Rescue CD to rescue data
- you can't use the Acronis True Image Boot CD (which is also Linux based of course)
- you can't use Crystal Disk Info in Windows to judge your SSD health (doesn't show the disk)
- you can't even install Windows 10 from the normal installation media without putting special drivers on an additional USB stick.
Well done Lenovo. Putting a machine that only has a single disk and cannot be expanded to two disks in RAID mode, that is quite a feat.

---

