---
title: "How to solve the grub install error when installing Ubuntu17.10 alongside Windows 10"
date: 2017-12-25
forum: Installation &amp; Upgrades
---

### Post by navajyoth814 on 2017-12-25
I've been trying to dual boot Ubuntu 17.10 alongside a preinstalled Windows 10 (which I don't want to remove) in a Dell Inspiron 5567 (find attached the specifications). An error pops up at the end of installation of grub2 package that roughly says grub install to /dev/sda failed - this is a fatal error. I've referred to multiple threads addressing the issue and none of the solutions works for me. 

When I tried for the first time, it worked during which I created root partition and home folders separately. But the bootloader was not proper as it booted directly to Ubuntu without showing boot options. Hence I decided to reinstall it and it never worked after that (tried almost 20 times as of now). 

Help me out [I'm not much familiar with dualbooting]  

Kindly tell me if further information is required.

[ATTACH=CONFIG]277933[/ATTACH]  
[ATTACH=CONFIG]277934[/ATTACH]

---

### Post by oldfred on 2017-12-25
You are not showing any Linux partitions?
What video card/chip does your system have? If nVidia you will need nomodeset.

See link in my signature for general UEFI install instructions.

Many Dell have had to have UEFI updates, and if SSD, SSD firmware updates.
With Dell you also have to turn RAID off and use AHCI, but install Windows AHCI drivers first.

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en
[/URL]
 Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en) 

[URL="https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en"]
[/URL]

---

### Post by sudodus on 2017-12-26
It seems your computer works well, when booted from a USB drive.


1. A temporary emergency solution would be to get a [fast USB 3 pendrive](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed) and install a **persistent live** system using [mkusb](https://help.ubuntu.com/community/mkusb).

Do **not**  make a full upgrade of that system (it will probably overload the overlay system and make it fail). But you can update it with ```
sudo apt update
``` and install the particular program packages that you need for your data analysis with

```
sudo apt install package1 package2 ...
``` and do your job.


2. An alternative is to make a **full installation** (install Ubuntu **into the USB 3 pendrive** like it would be installed into an internal drive). There is a rather detailed description at the following link,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

Such a full installation is more stable than a persistent live system and it can be fully updated and upgraded. But it can be corrupted by Windows, when it is doing major upgrades. So do not boot Windows, when the Ubuntu USB pendrive is plugged in.

Good luck :-)
sudodus

---

