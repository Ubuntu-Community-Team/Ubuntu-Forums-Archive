---
title: "Windows 8 Pre-installed laptop (UEFI) and Ubuntu Ubuntu 14.04 LTS problem"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by LordBerre on 2014-05-28
Hi,

I have installed Ubuntu 14.04 on my pre-installed Win8-laptop. The installation is successful, but Grub does not show up in the EFI-list in bios (and Win8 just boots directly). I tried the Repair-tool, i attached the logs from that. I tried reinstalling Ubuntu several times with no luck.

Attempt 1: [https://drive.google.com/file/d/0B_yldGPiPnJ2Q1N1WGMxY05kVDQ/edit?usp=sharing](https://drive.google.com/file/d/0B_yldGPiPnJ2Q1N1WGMxY05kVDQ/edit?usp=sharing)
Attempt 2: [https://drive.google.com/file/d/0B_yldGPiPnJ2d2lIRS1vd3Byb2c/edit?usp=sharing](https://drive.google.com/file/d/0B_yldGPiPnJ2d2lIRS1vd3Byb2c/edit?usp=sharing)

The only difference between these two logs is that the 2nd attempt I setup 2 additional partitions for swap/boot. Can anyone point me in the right direction?

Laptop: ASUS N550JV-CN283H
This is what the BIOS looks like: [http://www.tonymacx86.com/attachments/mavericks-laptop-support/79341d1389294763-mavericks-asus-n550jv-cn150h-bios.jpg](http://www.tonymacx86.com/attachments/mavericks-laptop-support/79341d1389294763-mavericks-asus-n550jv-cn150h-bios.jpg).

Secureboot/fast boot is disabled.

Kind Regards,
LordBerre

---

### Post by oldfred on 2014-05-28
When you turn on CSM mode that is BIOS not UEFI. Better to have that off, although some systems need that on, but still boot in UEFI mode for Intel video to work correctly.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And it does not look like grub correctly installed in BIOS boot mode as it then needs a 1 or 2MB unformatted partition with the boot flag to install grub2's boot loader to the protective MBR correctly.

Better to install in UEFI mode. And always boot in UEFI mode. How you boot installer is how it installs. UEFI & BIOS are not compatible and once you start booting in one mode you cannot change to other mode without rebooting. Or you cannot use grub menu to choose another system unless installed in the same boot mode.

Boot-Repair can convert a BIOS install to UEFI.

Most desktops do not need /boot as a separate partition unless a server type install using RAID or LVM. Having some swap is recommended but if you have 4GB of RAM or more you may never use swap, so 2 or 3GB of swap is all you may need.

See also links in my signature.

---

### Post by mikeyinid on 2014-05-28
My laptop came with UEFI enabled and W8, I wiped everything, booted into BIOS and switched to legacy and reinstalled everything. Might not be necessary but on my machine just switching to legacy, W8 wouldnt boot.

---

### Post by LordBerre on 2014-05-28
Thanks for the replies.

oldfred:

> [COLOR=#000000]When you turn on CSM mode that is BIOS not UEFI. Better to have that off, although some systems need that on, but still boot in UEFI mode for Intel video to work correctly.[/COLOR]
If i disable CSM I can't boot from anything other than "Windows Boot manager", no USB/DVD or anything. So am I not forced to install ubuntu with CSM enabled? Is there a way to do it anyway or can I convert from BIOS>UEFI after installing with Legacy, like you mentioned?

> [COLOR=#000000]And it does not look like grub correctly installed in BIOS boot mode as it then needs a 1 or 2MB unformatted partition with the boot flag to install grub2's boot loader to the protective MBR correctly.[/COLOR]

Not sure I had that free space.. I'll make sure to have that when I reinstall next.

---

### Post by LordBerre on 2014-05-28
So I guess the main problem is that my BIOS does not detect the Ubuntu-USB as an EFI-system? Since it doesn't show up when I'm running it in UEFI-mode.. Is there a way around it, would burning Ubuntu to a DVD be worth a try? Or anything easier (I don't have any CD's).

---

### Post by oldfred on 2014-05-28
It does not fit on a CD anymore. Flash drives are really preferred, but a DVD will work.

UEFI should see it. There may be a UEFI/BIOS setting to turn on USB ports when in UEFI mode.

You should see two entries, one UEFI and one something else that is BIOS, but often is not clear.

Boot-Repair can convert a BIOS install to UEFI and vice-versa, if correct gpt partitions are available.
For UEFI you need the efi partition, only one per hard drive.
For BIOS you need a unformatted 1 or 2MB partition with the bios_grub flag.

What system is this?

---

### Post by ubfan1 on 2014-05-28
Try disabling the "Launch CSM"  With Secure boot disabled too, that was all my Asus X200 needed (well, I could not permanently change the boot order, so maybe you have to catch it with the efi boot menu and pick the usb).

---

### Post by ubfan1 on 2014-05-28
Just found that by saving (F10) just after changing the boot order, the order was kept.

---

### Post by LordBerre on 2014-05-29
I found this thread: [http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383). It seems some other people with the same laptop are having the same issue with the USB not being detected when using UEFI-mode, and it seems burning to a DVD is worth a try also. I don't have any features for USB detection in EFI-mode or anything like that, looked everywhere in the BIOS.

I take it the repairtool can NOT convert my installation from BIOS>UEFI, considering this the below errors. And it wants me to go EFI-mode which I can't... So I'll go for the DVD and we'll see what happens.
[SIZE=2]```
Reinstall the grub-efi of sda9
grub-install: error: /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory.
grub-install : exit code of grub-install :1
Error: no grub*.efi generated. Please report this message to boot.repair@gmail.com

Add /mnt/boot-sav/sda9/boot/efi efi entries in /mnt/boot-sav/sda9/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda9/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /mnt/boot-sav/sda9/boot/efi/EFI/Boot/bootx64.efi
sda1/bootx64.efi already added
sda1/bootmgfw.efi already added

---- Grub-install verbose
/usr/sbin/grub-install:  1: /usr/sbin/grub-install: cannot create  n\F0\F0TT@T@DDP\E5td\8C\D2\8C\D2L\8C\D2Ll9l9Q\E5tdR\E5td\F0=\F0=n\F0=n/lib64/ld-linux-x86-64.so.2GNUGNUm:  Directory nonexistent
+ ELF @@@@@@\F8\F888@8@@@d:d: \F0=\F0=n\F0=n\9E{ \81 
/usr/sbin/grub-install: 1: /usr/sbin/grub-install: ELF: not found
/usr/sbin/grub-install: 2: /usr/sbin/grub-install: Syntax error: ")" unexpected
--------
/usr/sbin/grub-install : exit code of grub-install :2
---- End of grub-install verbose


chroot /mnt/boot-sav/sda9 efibootmgr -v
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```[/SIZE]

> Try disabling the "Launch CSM"  With Secure boot disabled too, that was  all my Asus X200 needed (well, I could not permanently change the boot  order, so maybe you have to catch it with the efi boot menu and pick the  usb).
The problem for me is that the USB is not even visible at all when CSM is disabled, the boot order is not an issue for me. Secure/fast-boot are already disabled.

---

### Post by oldfred on 2014-05-29
Also this thread.
  Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)

---

### Post by LordBerre on 2014-05-30
I burned Ubuntu to a DVD and my BIOS automatically detected it as an EFI-device and i reinstalled it. I can now boot up dualboot Ubuntu and Win8. Success!

Thanks for the help here. It made me figure out that my laptop just didn't see the EFI-functions on my USB  :) To much reading on other threads confused me to use Legacy mode since several guides recommended it. Again, thanks!

---

