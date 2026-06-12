---
title: "Invalid EFI file path"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by Ordanini on 2013-03-12
I've been looking for solutions to resolve the "Invalid EFI file path" error, and I've found a dozen - changing menuentries of grub file, installing rEFInd, using boot-repair etc -  but none of them worked for me.

I have an ASUS-UX31A ultrabook with Windows 7 inside. I've installed Ubuntu 12.10 alongside Windows 7. After that, I've rebooted and when I selected "Windows 7 (loader)", it appears this hell message "Invalid EFI file path".

I've tried to run boot-repair, but I think it didn't work. The error persists. Here is the log: [http://paste.ubuntu.com/5608344/](http://paste.ubuntu.com/5608344/)

Any idea?

My best regards,

---

### Post by oldfred on 2013-03-12
If you go into BIOS and change from UEFI boot to BIOS/CSM mode you may actually be able to boot Ubuntu, but then not Windows.
Both Windows & Ubuntu have to be either UEFI boot mode or BIOS/Legecy boot mode. And how you boot installer is how it installs, so it looks like you booted Ubuntu installer in BIOS mode not UEFI mode.

It looks also like you have a small SSD, which may be then an UltraBook with RAID? That adds complications.

If you have Windows 7 then you do not have secure boot issues, but otherwise it is the same as the new Windows 8 UEFI installs.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
        HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

UltraBooks also have dual video and need bumblebee.
      
 Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
[http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889](http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)


  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Details in post #10 on an Intel SRT install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

