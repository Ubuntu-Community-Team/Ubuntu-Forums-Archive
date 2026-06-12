---
title: "32-bit and 64-bit Ubuntu versions on same hard disk"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2015-04-13
I have been using Ubuntu since 10.04 and upgrading as new releases came along without any problems. Even though my laptop has a 64-bit processor I have stayed with the 32-bit versions in order to just upgrade my existing setup without the hassle of a new installation and because the forums all suggested that the advantages of the 64-bit system were not that great. However I have noticed that some magazines have stopped including 32-bit versions of software on their DVD's and recently Google have announced that the 32-bit version of its Linux 32-bit Android Emulator (in the Android ADT) is deprecated and will in future only work with 64-bit systems.

So I have decided to install a 64-bit Ubuntu 14.10 version alongside my 32-bit Ubuntu 14.04 system on my laptop. I also have a small Windows-7 partition which I want to keep because a) I might need it one day for something and b) I paid for it with the laptop. My hard disk looks like this now;

/dev/sda1  ntfs    PQSERICE       20 GiB
/dev/sda2  ntfs    SYS Reserved  100 MiB
/dev/sda3  ntfs    Packard Bell      71 GiB
/dev/sda4  Extended                 840 GiB
  /dev/sda8  ext4   This is ready for 64bit sys  352 GiB
  /dev/sda7  ext4    Existing 14.04 32-bit and mount point         472 GiB
  /dev/sda6 linux swap   Not use                                             7.85 GIB
  /dev/sda5 linux swap   This is used by sda7                           7.85 GIB

I have a Multiboot-DVD from Linux Welt, a German Linux mag, with a bootable DVD version of Ubuntu 14.10 64-bit and can be used to install the OS. When I boot the DVD set up the WLAN and choose install Ubuntu 14.10 64-bit I am asked if I want to install over the Windows or Ubuntu partitions or reformat the whole disk or "Something else". I choose "Something else" and I get a Gparted sort of picture of the hard disk showing all of the partitions. If I highlight /dev/sda8, where I want to install, and then click on install I get the warning "Es wurde kein Root-Dataisystem festgelegt. Bitte beheben Sie dies im Partitionierungsmenü" which translates to "There is no specified root Dataisystem. Please fix this in the partitioning menu" I am not sure what to do after this warning. I do not want to write onto or format anything but sda8 and the spare linux-swap on sda6.

If anyone could help me with this I would be very grateful.

---

### Post by Elfy on 2015-04-13
something else, mount point / 

[IMG]http://i.imgur.com/0pxuVzf.png[/IMG]

---

### Post by grahammechanical on 2015-04-13
I don't think it has been mentioned but we click Change and then we get the Edit Partition dialog. We set a Use as, tick the Format box and set a mount point of / and then click OK. Now after double checking that we are installing into the correct partition and that the Grub boot loader will be install where we want it to go, we click Install.

Regards.

---

### Post by stepheny on 2015-04-14
Thank you both very much. Just one more thing before I bite the bullet and install. If I leave the "Device for boot loader installation" at /dev/sda will the existing Grub be edited to show the new Ubuntu partition as well as the existing one and Windows?

---

### Post by plucky on 2015-04-14
> **stepheny said:**
> Thank you both very much. Just one more thing before I bite the bullet and install. If I leave the "Device for boot loader installation" at /dev/sda will the existing Grub be edited to show the new Ubuntu partition as well as the existing one and Windows?

The Grub for the new installation will take over the booting and it will boot to 14.10 as default. It should also find the other installations and give you the option to boot them from the Grub menu.

If you want, you can choose not to install grub to the bootloader and when you boot the 32-bit 14.04 and run ```
sudo update-grub
``` it will find the new install and you can then select it from the Grub menu.

Good Luck

---

### Post by stepheny on 2015-04-14
Great. I have now installed Ubuntu 14.10 64-bit alongside 14.04 32-bit. I can now migrate to the 64-bit OS in my own time. 

Thanks again everyone for your help, I have marked the thread solved.

---

