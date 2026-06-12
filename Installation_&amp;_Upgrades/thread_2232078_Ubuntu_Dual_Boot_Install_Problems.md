---
title: "Ubuntu Dual Boot Install Problems"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by bobnewbie2 on 2014-06-29
Hi everyone,


I'm currently trying to dual boot windows 7 and Ubuntu 14.04 x64 on my laptop, and I'm having a bit of trouble. My computer model is a ~2 year old Sony Viao 13" S series that uses an Insyde H20 UEFI system, and windows is already installed: I'm trying to install Ubuntu via an external hard drive set up with the Universal USB installer. When I boot to the hard drive, I can get to the "try Ubuntu/Install ubuntu/check disk" screen, but selecting those top options yields nothing but a black screen and blinking cursor.


After digging around on the internet a bit, I tried playing with the acpi and other settings, but nothing worked. No splash revealed this traceback:




dump stack
panic
printk
mount_block_root
prepare_namespace
kernel_init_freeable
do_early_param
rest_init
kernel_init
ret_from_fork
rest_init




(this is with noapic)




Other potentially relevant settings:
this laptop has a dual-GPU Nvidia setup
8GB RAM 
Samsung 830 evo SSD.




Google hasn't turned much up. Any ideas?

---

### Post by oldfred on 2014-06-29
Even with UEFI as the BIOS replacement most Windows 7 systems were installed in CSM/Legacy/BIOS mode.

May be best to see details. Sony's seem to have modified UEFI to only boot Windows, so many rename the Windows boot file to actually be shim or grub and then boot Windows from grub menu.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Windows 7 is in UEFI mode, then you will not have secure boot issues nor the fast boot issues that Windows 8 has. Just do not hibernate Windows 7.

      
 EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
      Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[URL="http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570"]http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570
      [/URL]         HOWTO: Sony Vaio Pro 13 DualBoot (Win 8 + Ubuntu Trusty 14.04) SecureBoot Wifi LVM
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580)
 Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
With encryption but you do not have to
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)

    
 [URL="http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570"]
[/URL]

---

