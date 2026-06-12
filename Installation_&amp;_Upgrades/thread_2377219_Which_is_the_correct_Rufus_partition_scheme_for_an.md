---
title: "Which is the correct Rufus partition scheme for an older laptop (with BIOS)?"
date: 2017-11-10
forum: Installation &amp; Upgrades
---

### Post by Bobby_James on 2017-11-10
Can someone please confirm the correct partition option in Rufus for making an installation USB for 16.04.

I have a Samsung Ultrabook which is about three years old. It has a BIOS menu which allows one to select UEFI or CSM. The machine will become a dual boot with Windows 8 and 16.04.

Is it: 
MBR Partition Scheme for BIOS or UEFI (as the Samsung is an older machine). 
MBR Partition Scheme for UEFI
GPT Partition Scheme for UEFI

Also, if I deleted Windows 8 and made the entire partition 16.04, would this alter the partition scheme in Rufus?

Thanks!

---

### Post by oldfred on 2017-11-10
Only a few systems does it matter.
Any machine with UEFI is a newer machine. :) 
 Windows 8 release date: October 26, 2012. And then UEFI became the Windows standard.


But if a 3 year old system you will want to install in UEFI boot mode on a gpt partitioned drive.
As Windows 8 pre-installed is UEFI and always best to have all systems in same boot mode.

If you want to delete Windows 8, be sure to do a full image backup. Many seem to want to make the leap to Linux but find that one program or game that only runs in Windows that they must have, and then want to reinstall Windows. 

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

What model Samsung:

 Samsung w/ Phoenix Tiano SecureCore
[http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267](http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267)
Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)

---

### Post by Bobby_James on 2017-11-11
Thanks for the reply - I will use GPT partitioning. 

What I don't understand is why the official Ubuntu site recommends MBR partition scheme for UEFI. See [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#3](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#3)

Any ideas?

---

### Post by oldfred on 2017-11-11
The standard Linux flash drive installer is for both UEFI and BIOS.
Typical install flash drive is either one FAT32 partition or the dd image which is a hybrid DVD/flash drive.

With gpt to boot in BIOS mode you must have another partition bios_grub for the flash drive.

UEFI will boot from MBR(msdos) partitioned drive, but partition must be seen as FAT32 with boot flag. 
BIOS needs a boot loader in the MBR (first sector), the installer uses syslinux boot loader which is also a Windows type boot loader for BIOS boot.

I now only use gpt, but most of my flash drives are full installs of Ubuntu & I use grub2 to loopmount boot an ISO directly. Bit more advanced but then possible to boot from my HDD to install to SSD or vice-versa.

 ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 
      
 gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [URL="http://en.wikipedia.org/wiki/Master_boot_record"]http://en.wikipedia.org/wiki/Master_boot_record

      [/URL]
 Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/) 
    [URL="http://en.wikipedia.org/wiki/Master_boot_record"]
[/URL]

---

