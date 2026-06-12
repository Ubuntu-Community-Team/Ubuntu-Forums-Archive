---
title: "I have installed ubuntu 13.10 but I can't get the dual-boot to work"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by luca8 on 2014-03-15
So, I decided to try Linux after a long time. I have an HP Laptop with 750GB of HD, with pre-installed Windows 8.1
First of all, I created a new partition called U:\ of 30GB
I installed Ubuntu 13.10 with a Live USB Key (I used unetbootin and put the .iso file downloaded form the offìcial ubuntu web site into the usb key).
I selected the U:\ partition, mounted it on :\  and everything seemed to work, the installation was succesfull.
That being said, I unfortunately can't access to ubuntu: when I turn the laptop on, windows 8.1 is booted with no other choice, there is no dual-boot whatsoever.
I looked for some solution on the internet, I tried with boot-repair, nothing. I also tried with EasyBCD, no results aswell. I turned the "Secure Boot" option off in the BIOS but nothing changed, so now I'm running out of options.
What can I do to get the dual boot option to work, so that I can chose what OS I'd like to use every time I start my PC?

Sorry for the bad English, It's not my main language and all I know, I learned from books.

---

### Post by ahepas1999 on 2014-03-15
Did you install GRUB on MBR? It should be installed on /dev/hda during the installation process

---

### Post by ubfan1 on 2014-03-15
You have a UEFI machine, with a gpt partitioned disk, so the grub bootloader will get placed into <EFI partition>/EFI/ubuntu.  Additionally, the installation should have made an entry into the machines nvram memory to select that bootloader, but it is not the default loader.  You can select the efi menu at boot time with a function key (or ESC, or DEL, varies by machine) to select the boot device/OS.  Select "ubuntu" and see if that works.  If it does, you can change the default boot selection with the efibootmgr program, or you can just continue to use the efi menu.

---

