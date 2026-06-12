---
title: "Install 16.04 from USB thumb drive - black screen w/ cursor"
date: 2017-07-19
forum: Installation &amp; Upgrades
---

### Post by Xinghao_Chen on 2017-07-19
I downloaded the 16.04 AMD 64-bit desktop iso image (~1.4GB) and copied it over to a 4GB clean USB thumb drive. Then powered on my T520 with F12 key to select boot from the USB thumb drive. It followed with a black screen which has an cursor shown at the top-left corner. It stayed on this black screen for several minutes showing no sign of progressing before I turned off the T520. 

What did I miss in preparing the ISO on to the USB thumb drive?

My T520 has a 128GB SSD as the C drive installed with Windows 10 Pro, a clean 32GB SSD on the internal mSATA port intended for Ubuntu, 8GB DDR3 RAM.

---

### Post by oldfred on 2017-07-19
You say copy, but did you use installer, which formats USB flash drive, extracts ISO and makes it bootable?
If new system it should be UEFI. Is Windows installed in UEFI mode?
You need 32GB partitioned as gpt and should have an ESP - efi system partition on it, but that may not be ever used. Grub in UEFI install only installs a new folder into the existing ESP in drive seen as sda, normally next to the Windows folder in the ESP.

What video do you have? If nVidia or AMD you may need nomodeset boot option.
So not sure if booting issue, or video driver issue.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
            Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
            At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 
    
Only use something Else install option, and make sure Windows fast start up is off, even though that may not be required since installing to a second drive. Installer may not make 32GB drive gpt and any auto install option, usually does not optimally create partitions.
You may not need swap, but I suggest a small 2 or 3 GB swap. Installer will probably use 8GB for swap if you use any auto install option.
See also the link in my signature for general install instructions.

Issues often common by brand and similar models. So these may also discuss specific Lenovo issues.
       Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208) 
            T540 works but UEFI settings critical or it may brick reset w/ Switching "OS Optimized Defaults
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)

---

### Post by Xinghao_Chen on 2017-07-19
Thank you for your reply.

I did not do anything else other than download the ISO image and move/copy it on to a clean 4GB USB thumb drive. I will check out the links provided in your note. Previously I had made 10.xx and 12.xx ISO on DVD disks and don't recall doing anything else to make them bootable. I thought it would be the same and simple by dropping the ISO onto the thumb drive.  

The windows 10 file system on my T520 is formatted in NTFS and so is the 32GB SSD in the mSATA port. My previous Ubuntu installs (10,xx 12.xx 14.04) all worked well with NTFS and convenient for my use for file transfers, etc.

---

