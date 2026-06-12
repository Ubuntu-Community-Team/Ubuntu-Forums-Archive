---
title: "Grub Not Loading Ubuntu"
date: 2016-11-16
forum: Installation &amp; Upgrades
---

### Post by mordok19 on 2016-11-16
Hi All, I'm new to Ubuntu. I've installed Ubuntu 16.10 on an external HDD when I reboot I get into Grub 
Rescue. I've tried using the Boot-Repair to solve it but it still comes up with the error. I've uploaded the Boot-Repair to [http://paste2.org/ankKBfzm](http://paste2.org/ankKBfzm) 

Could someone help??

Thank in advance

Mordok19

---

### Post by yancek on 2016-11-16
Your boot repair output shows the 298GB drive (sdd) has Grub installed in the MBR and it does have entries for windows in the grub.cfg file.  Do you have that drive set to first boot priority in the BIOS.  It also shows that you have windows code in the MBR of the first drive (sda 298GB drive) which seems to have Easy BCD or Grub4Dos to boot.  You mention an error but not what it is, just a grub rescue prompt?

---

### Post by oldfred on 2016-11-16
Are you booting grub from sdd, the external drive?
You seem to show lots of grub installs to partition boot sectors (PBR). That is not recommended by grub. And with multiple drives you can always install to the MBR of a drive.
EasyBCD is the one that uses the very old grub4dos to chain load to grub. And it wants grub in a PBR, but that is only required if you only have one drive.

You also show Radeon driver? I do not know AMD, and if that is correct video driver or not.
       [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).

---

### Post by mordok19 on 2016-11-16
Thanks for your replies. When I installed ubuntu I chose my external HHD to store grub so I could press the F12 button and tell it to boot from my external HDD. I'm running Windows 7 on my PC with EasyBCD boot loader as I also have Windows Vista installed on a second partition. When I boot from my external HDD it boots straight into Grub Rescue. When I type ls I get a list of HDD's but using ls (sda) or ls (sda,msdos) I get a unknown partition.

---

### Post by oldfred on 2016-11-16
There used to be an issue with very old BIOS not booting if boot files are beyond 137GB on a drive.
If internal drive the old IDE mode often caused similar issue.
But external drives have also had similar issue, not sure if BIOS or just something with USB driver.

I might just try shrinking your / (root) on sdd to less than 100GB with gparted from live installer. That should be relatively quick and an easy test to see if that is issue. (About half of those I have suggested this, found it worked, so no guarantee.)
If that works you can use rest of drive for /home, /mnt/data or another NTFS data partition for shared data.

---

