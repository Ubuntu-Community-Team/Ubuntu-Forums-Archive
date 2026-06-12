---
title: "Installer does not list desired partitions"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by kimdino2 on 2013-11-30
Hi folks,
I am trying to install Ubuntu but the installer is not offering my desired partition as an option.

My system:
'fdisk -l' gives:-
Disk /dev/sda: 1000.2 GB, 1000200658432 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953516911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d54b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    48828415    24413184   fd  Linux raid autodetect
/dev/sda2        48828416    60547071     5859328   fd  Linux raid autodetect
/dev/sda3        60547072  1818359807   878906368   fd  Linux raid autodetect
/dev/sda4      1818359808  1935546367    58593280   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000380eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    48828415    24413184   fd  Linux raid autodetect
/dev/sdb2        48828416    60547071     5859328   fd  Linux raid autodetect
/dev/sdb3        60547072  1818359807   878906368   fd  Linux raid autodetect
/dev/sdb4      1818359808  1935546367    58593280   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00094ae3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    48828415    24413184   fd  Linux raid autodetect
/dev/sdc2        48828416    60547071     5859328   fd  Linux raid autodetect
/dev/sdc3        60547072  1818359807   878906368   fd  Linux raid autodetect
/dev/sdc4      1818359808  1935546367    58593280   fd  Linux raid autodetect

Disk /dev/sdh: 1000.2 GB, 1000200658432 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953516911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00074191

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *          63    19535039     9767488+  83  Linux
Partition 1 does not start on physical sector boundary.
/dev/sdh2        19535040    23438834     1951897+  82  Linux swap / Solaris
/dev/sdh3        23438835  1878914204   927737685   83  Linux
Partition 3 does not start on physical sector boundary.
/dev/sdh4      1878914205  1937503259    29294527+  83  Linux
Partition 4 does not start on physical sector boundary.

The mobo is a Gigabyte GA-MA790FX-DS5 which has six SATA slots. sd[a-c] are on slots 0-2 with my optical drive being on slot 3. sdh is on slot 4. Only slots 0-3 are bootable but I am able to boot a system on the fourth hard drive from a GRUB setup on the bootable slots.  The first three drives are RAID5, using 'md', and contain a Debian installation (which is not to be touched). I use the fourth drive for checking out other distros and as I am currently desiring to look at Steam I am trying to install 12.04 to it. sdh1 has been freshly formatted to take the installation though I plan to incorporate my previous installations (Vector 7) /home (sdh3) & opt/ (sdh4) contents.

When the Ubuntu installer reaches the 'Installation type' screen it shows 'This computer currently has no detected operating systems, what would you like to do?' at the top. Has the RAID caused it failed to detect the Debian installation? So I select the 'Something else' option.

The next screen, also labelled  'Installation type' has a list of all the partitions on sd[a-c] but does not show sdh. At the bottom of this screen is a dropdown labelled 'Device for boot loader installation' offering me all the partitions on sd[a-c], I cannot see an option to not install a boot loader, I do not want to risk upsetting my existing GRUB setup.

How might I proceed?

Thanks in advance, Kimdino

---

### Post by oldfred on 2013-12-02
The standard desktop installer does not have the RAID drivers. There are planning on adding them but with 12.04 you would use the Alternative installer with RAID or LVM. The newest version has LVM as an install option but not yet the RAID install option.

But since installing to sdh, you should not need the RAID drivers. Also the installer does not have an option not to install grub. You can only with manual install specify the MBR of sdh or if you have another copy of grub to boot with can install grub to a PBR - partition boot sector more as a throwaway. Using PBR is not recommended as grub has to convert to hard coded addresses and is less reliable.

If when in live mode install this and it should then see the RAID. Not sure if that carries over to installer or not.
 sudo apt-get install mdadm

      
 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

If drive is not directly bootable, then BIOS may not be reporting it and then installer will not be able to offer to install into it. You could temporarily plug into a bootable port, a USB port, or another system and install into that. Then from your boot in RAID add the correct boot stanza to boot the install in sdh.

---

