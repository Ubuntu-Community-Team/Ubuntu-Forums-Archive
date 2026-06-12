---
title: "Can't boot Ubuntu 15.04 after installation"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by conglomerate2 on 2015-06-16
Hi all,

I've decided to get rid of Windows 8.1 and install Ubuntu 15.04 instead. I don't know if I should have taken preliminary steps in regards to the UEFI/SecureBoot before installing, but I can't seem to boot into Ubuntu. 

This was my installation process:
1) Wiped all my windows partitions using Gparted from the bootable USB
2) Installed Ubuntu from said bootable USB, selecting the "Erase disk and install Ubuntu" option. 

The installation process went on fine, and asked me to reboot the computer to complete the installation. However, when I reboot, [these]("http://i.imgur.com/nc9VXKO.jpg") are the booting options I see. The ATA-HDD0 is my 256Gb SSD where I've installed Ubuntu and the USB Disk 3.0 is the bootable USB. When I select the SSD, nothing happens (goes back to the same screen). I've have performed a boot repair using boot-repair, and the problem still persists ([here]("http://paste.ubuntu.com/11724505/") is the log).

I've also tried redownloading the ISO, remaking the bootable USB, and reinstalling (as I thought my installation files may have been corrupted), but still nothing. If it's any help my computer is a Lenovo Thinkpad T430s.

Thanks for your help!

---

### Post by oldfred on 2015-06-16
Have you tried with secure boot off?  UEFI on, and CSM off.
You do have signed versions of kernel, so it should work with secure boot on.

Some vendors modify UEFI to boot by description of UEFI entry which is not UEFI standard. And they make only valid description "Windows".  In those cases we have work arounds to rename bootx64.efi which is the UEFI hard drive boot entry which still works, or if not using Windows you can copy grub or shim to the Windows efi boot file. System thinks it boots Windows description, but then really boots grub. If dual booting best not to rename Windows file as Windows will evenually update it and create issues again.

While not same model Lenovo, often UEFI is very similar with only difference is options present on various models.
       [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

            T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)

             lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)

You also have a lot of UEFI entries from efibootmgr -v list. You may want to houseclean some of those, especially those that are duplicates. Details of commands (somewhere) in link in my signature if interested. Also some details on renaming files.

---

### Post by conglomerate2 on 2015-06-16
Thanks for the reply! I have turned secure boot off, UEFI on, and CSM off and I now get this error message when selecting the SSD where Ubuntu is installed:

```
Failed to open \EFI\BOOT\grubx64.efi -800000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi -800000000000000E
Failed to load image
```

I have found a [post]("http://askubuntu.com/questions/597245/failed-to-open-efi-microsoft-boot-grubx64-efi-80000000000000e") with a similar error that was resolved by deleting the EFI/microsoft folder. Would you recommend doing this?

As soon as I get done with this problem I'll try to clean up the efibootmgr -v list..it does seem to be very messy.

---

### Post by oldfred on 2015-06-16
If you have grub or shim in /EFI/Boot then rename it to bootx64.efi and still boot hard drive entry.
Microsoft folder should not matter, I might back it up & delete it. But a few systems really want that entry to boot from and then we copy grub or shim into /EFI/Microsoft and rename the Windows efi boot file.

---

### Post by conglomerate2 on 2015-06-16
In my /EFI/BOOT folder, I had BOOTx64.efi and grubx64.efi . I backed up BOOTx64.efi and renamed grubx64.efi to bootx64.efi as you suggested. I still get the same "Failed to open/Failed to load" error... Am I supposed to change anything else? Thanks again for your help!

---

### Post by oldfred on 2015-06-16
Is the error like you posted saying grub? Or now that you renamed it does it say bootx64.efi?
You should be booting the entry that says hard disk. But you showed many entries in your UEFI so you may need to go into live installer and run this to see which is which.

sudo efibootmgr -v

That will show details of which file is really used to boot. Your UEFI may show that if it has more details than most.

---

### Post by conglomerate2 on 2015-06-17
Got it fixed! Turns out you were right the first time around, and I only had to rename to move the grubx64.efi from the EFI/unbuntu folder to the EFI/boot folder and rename it to bootx64.efi. It's just that my inexperienced self had done it on /sda2 the first time around (where there is a boot/efi folder too), and not on /sda1. [This]("https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair") post is a pretty good step by step guide to what I did to resolve my problem. Thank you so much for your time!

---

