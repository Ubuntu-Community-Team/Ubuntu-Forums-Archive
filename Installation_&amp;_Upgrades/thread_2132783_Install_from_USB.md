---
title: "Install from USB"
date: 2013-04-05
forum: Installation &amp; Upgrades
---

### Post by neutralise on 2013-04-05
I recently bought a samsung series 9 ultrabook (np900x4c-a05au) and am trying to install a linux distribution (dual boot) on it.

The machine won't boot from usb (no cd drive), I have disabled fast boot from the bios, used two different (ntfs formatted) usbs and tried all 3 usb ports.

I tried using unetbootin, universal usb installer, diskimager and linux live usb creator to make the image on the usb.

I tried using ubuntu, kubuntu and kali on the usb.

By pressing f10 I can see the usb in the boot menu, however the machine will not boot from the usb (even when disabling boot from hdd in the bios).

Does anyone know anything else I can try, or how to fix this?

---

### Post by oldfred on 2013-04-06
UltraBook complicates an already complicated UEFI install as Intel uses RAID which the desktop installer does not fully see, and you have optimus which many get working with bumblebee.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

    
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

      
 Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)

Dell but UltraBook

  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

### Post by neutralise on 2013-04-06
Firstly, thank you for an in depth reply.

> You will need to use the 64 bit version of 12.10 or 12.04.2 and from the  UEFI menu boot the flash drive in UEFI mode. That way it will install  in UEFI mode.
> Systems need quick boot or fast boot turned off in UEFI settings. Vital  for some systems. Best to backup efi partition and Windows partition  first.

Is the UEFI menu just my bios?
How can I boot a flash drive in UEFI mode?

---

### Post by oldfred on 2013-04-06
UEFI is the new BIOS, but it has a compatibily mode called CSM.
 Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 

From a UEFI menu with secure boot off and CSM off or UEFI on, but not secure boot UEFI on (settings vary), you should from UEFI have two choices to boot a flash drive. One will mention UEFI and the other legacy/BIOS/AHCI/CSM or something.

---

