---
title: "Error code 1962 - no operating system found"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by c-masini on 2015-09-25
Dear all,

I have seen other posts along this line - but none of the previous suggestions worked for me.
I have a Lenovo desktop (C445) which have a pre-installed windows8.
I have deleted all previous partitions and installed Ubuntu 15.04 installing it via USB.

I have followed this guide:
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)

I can go through all the installation steps - ie. all the way through to reboot.
But then, if I remove the USB I get the error message "ERROR CODE 1962 - NO OPERATING SYSTEM FOUND".
If I leave the USB on, the installation starts all over again on a loop.

I have tried many tests, with no success:
- install version 14.04 LTS;
- version 10.04 LTS - as suggested in other posts;
- entered various combinations of BIOS set up options (UEFI only / LEGACY only; SATA mode = IDE vs AHCI mode)
whatever I do, when rebooting I get the error code 1962.

I have tried boot repair - which gives me the report at this link:
[http://paste.ubuntu.com/12558258](http://paste.ubuntu.com/12558258)

I believe I am following all the right steps in the installation - but probably i am missing something in the setup of the hardware.
Any advice?
Thanks, Cristian

---

### Post by coffeecat on 2015-09-25
Not a Resolution Centre thread.

*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2015-09-25
Most now seem to copy grubx64.efi into /EFI/Boot and rename to bootx64.efi and boot a hard drive entry. If hard drive entry UEFI boot entry does not exist, you may have to also create that.

T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by c-masini on 2015-09-26
Hello oldfred. I solved the issue by following one previous thread of yours. Thanks so much. Cristian

---

### Post by c-masini on 2015-09-26
By the way, how do I set this thread as SOLVED? :-D

---

### Post by PaulW2U on 2015-09-26
> **c-masini said:**
> By the way, how do I set this thread as SOLVED? :-D
Above your first post in this thread you'll see "Thread tools". Click that and you'll see the option to mark the thread as being Solved.

---

