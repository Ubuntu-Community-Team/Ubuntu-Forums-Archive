---
title: "Partitioning &quot;/boot&quot; partition Ubuntu/Windows8"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Damascushead on 2013-02-06
I just got a Lenovo IdeaPadU510 preinstalled with Windows8, and like many, am attempting to dual boot with 12.10
 
To recap what I have done so far:
 
-Allocated free space on HDD
 
-Went in to bios and disable "secure boot" and UEFI. (Would not allow to boot from liveUSB unelss I switched to Legacy mode)
 
-Manually partitioned / (root), /home, swap, and /boot, under the "Something Other" option.
 
 
My question is, do I really have to create a /boot partition in order to dual boot? Or do I tell it to boot from the windows8 EFI boot partition that already exists? When I hit 'install' on the four partitions mentioned above it says that I may encounter disk error unless I create some sort of OEM partition. 
 
I have been following a few tutorials:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
 
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
 
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)
 
Yet none have been specific about this.
 
Any help would be appreciated. Thanks

---

### Post by oldfred on 2013-02-06
Is it saying you need a bios_grub partition? If so you are installing in BIOS mode not UEFI mode. A few computers have to be installed in BIOS mode and then use Boot_Repair to convert from BIOS to UEFI by un-installing grub-pc and installing grub-efi.
Generally a separate /boot is not required. And with UEFI the grub-efi installs its boot files into the same efi partition that Windows uses. The efi partition is like the MBR but allows many installs to each have folders and boot. But secure boot has compliated that a lot.
Some computers do not work with UEFI due to UEFI bugs, some will work with some effort and some work well.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
If Samsung check model number as some can only be installed in legacy/CSM mode or computer may be bricked.
Kernel updates being released and Samsung needs to update UEFI/BIOS.

    Lenovo's that worked (eventually)
       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Damascushead on 2013-02-06
Oldfred, I am doing as you suggested.

I have one of the few machines that can't install from EFI mode. In fact, it will not even give me the option to boot from USB or CD unless I am in Legacy mode. 

I am (as I write this) manually partitioning Ubuntu with /boot, /(root), /home, and swap partitions in legacy BIOS mode to install GRUB. I will then run the boot repair, to get grub-efi instead of legacy. I will let you know the outcome.

---

### Post by Damascushead on 2013-02-11
Thank you oldFred. I finally got the dual boot configured. I am thinking of writing up a tutorial of what I learned in the process. 
 
There were some hiccups with the way my UEFI boot up was working with the live boot USB. Got it working after a strange configuration and a boot-repair.
 
:p

---

### Post by oldfred on 2013-02-11
Glad you got it working.

Some have a lot of issues and for a new user it can be too much. But process is improving over time and each Ubuntu/grub update and as vendors fix issues with UEFI.

---

