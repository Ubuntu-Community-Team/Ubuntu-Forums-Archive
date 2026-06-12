---
title: "Dual Booting Win 7/Ubuntu with Intel SRT"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Jesmaail on 2012-10-27
I'm currently running Windows 7 on a 1Tb HDD with Intel smart response technology caching a 64gb SSD.

Is it possible that I will be able to install Ubuntu onto a separate hard drive and boot with no problems or will the fact it was set up in raid affect the install or GRUB.

Want to check before I attempt it as I am a touch timid on messing with my SRT set up.

Thanks.

---

### Post by Jesmaail on 2012-10-29
Has no one tried dual-booting like this?

---

### Post by oldfred on 2012-10-29
If you are installing to another drive you should not have any issue. With RAID you do need extra drivers that are not standard with the Desktop install, but can easily be added afterwards.

Herman now uses the Alternative installer which includes RAID drivers. Installer has not changed much between versions and even text installer is not all that different than gui version.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Some with Intel SRT. Either removing SRT and installing Ubuntu to SSD, or installing to same hard drive as Windows by turning it off & then back on after install. But if installing to a third drive you should not have any of these issues.

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by Jesmaail on 2012-12-16
When using either normal or alternate installer I am unable to see any drives apart from my third Hard drive, is it dmraid that will allow me to view these, if so how do I activate it in the installers.

---

### Post by Jesmaail on 2012-12-16
Previous posts may have been a bit vague, what I'm trying to do is get it so the end result is that I can boot into either Win7 or Ubuntu from GRUB, with Win using the SRT raid drives and Ubuntu on my third hard drive

---

