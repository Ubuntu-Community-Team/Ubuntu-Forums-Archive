---
title: "&quot;No working init&quot; problem at installation"
date: 2022-09-25
forum: Installation &amp; Upgrades
---

### Post by rkoppany on 2022-09-25
Hello!

I have a problem when I try to install Ubuntu 22.04 Desktop.

I have a Dell Inspiron 5558. The pendrive is noname, but usable, I installed another OS with it already (as a try after I couldn't Ubuntu), so now there is Deepin OS on the laptop.

In advance I write some info what would be the first thought for everyone:
[LIST=1]
[*]I tried both UEFI and Legacy
[*]I tried downloading the ISO again, from all mirrors
[*]Checksum is correct
[*]Secure boot, fast startup all turned off
[*]In boot sequence the usb stick is the first
[*]Tried to write the usb with BalenaEtcher, Ventoy, Rufus
[*]Tried another usb stick too
[*]Tried another usb port
[*]Tried to install on another laptop (!!!) too!
[/LIST]

So booting into grub is okay, but when I go to "Try or Install Ubuntu", or "Ubuntu (Safe Graphics)", or "OEM Install (for manufacturers)", in every case I get a big message saying this:
```
0.463350 - Initramfs unpacking failed: ZSTD-compressed data is corrupt
0.605267 - Failed to execute /init (error -2)
0.605355 - Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
0.605398 - CPU: 3 PID: 1 Comm: swapper/0 not tainted 5.15.0-43-generic #46-Ubuntu
0.605422 - Hardware name: Dell Inc. Inspiron 5558/086DKN, BIOS A18 12/30/2019
0.605444 - Call Trace:
0.605454 - <TASK>
0.605463 - show_stack+0x52/0x58
0.605478 - dump_stack_lvl+0x4a/0x5f
0.605493 - dump_stack+0x10/0x12
0.605506 - panic+0x149/0x321
0.605519 - ? putname+0x55/0x60
0.605533 - kernel_init+0x14c/0x150
0.605547 - ? rest_init+0x100/0x100
0.605560 - ret_from_fork+0x22/0x30
0.605575 - </TASK>
0.605608 - Kernel Offset: 0xcc00000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
0.605642 - ---( end Kernel panic - not syncing: No working init found. Try passing init= option to kernel. See Linux Documentation/admin-guide/init.rst for guidance.
```

Could someone tell me the solution for this?

Thank you in advance!

---

### Post by MAFoElffen on 2022-09-25
Re-download the ISO image. After downloading it, check the  md5sum of the ISO. It looks like the previosly downloaded image was bad.

---

### Post by rkoppany on 2022-09-26
This is why I started with the list.
I already tried it. I downloaded the ISO from all sources, on different computers and places (even with more stable internet connection), but it didn't help, and the checksum was always correct.

---

### Post by MAFoElffen on 2022-09-26
Yes. I read your list. I looked up the specs on your laptop. I am familiar with your laptop. I am still certified for onsite warranty repair of Dell, Lenovo and HP computers. I know that that laptop is compatible with Ubuntu. In fact, when on calls, besides my two Dell USB thumbdrives that I carried for MB Branding and Dell Diagnostics, I carried an Ubuntu LiveCD USB drive to help me with diagnostics...

I know that model has 4th or 5th Intel Processors with onchip Intel Graphics and discrete NVidia Graphics... So to boot the LiveCD and after installing, the first boot after installing (before installing the NVidia driver) that you need to add a 'nomodeset' boot parameter in the Grub Boot menu. And you need to use Xorg XServer instead of trying to use Wayland. NVidia does not play well with Wayland.

I know from over a decade of supporting Ubuntu users trying to install Ubuntu, that when I see a kernel dump like that, that the first thing to suspect is a bad image, either from the download, or from burning the image to cd or usb. 

Next is brand of USB. Though Dell is not real picky about USB thumb drive brands, but sometimes... On the newer LiveCD, at the startof boot, after about 4-5 seconds, if you press the escape button, it may say "press control-c to abort file check" and do nothing to let it do a file check. That will check the files and filesystem of the written image...

Next is device errors. This could be from an outdated BIOS version or GPU. Ensure your BIOS version is "Version A18, 19 Feb 2020" <-- This was a new Critical BIOS firmware update for your laptop...
[https://www.dell.com/support/home/en-us/product-support/product/inspiron-15-5558-laptop/drivers](https://www.dell.com/support/home/en-us/product-support/product/inspiron-15-5558-laptop/drivers)

---

