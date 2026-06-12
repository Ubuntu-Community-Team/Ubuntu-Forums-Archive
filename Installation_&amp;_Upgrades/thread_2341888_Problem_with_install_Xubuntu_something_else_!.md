---
title: "Problem with install Xubuntu something else !"
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by sebastien95 on 2016-11-01
Hello !

I have a HP Stream laptop, it contains a 32G MMC SSD with EFI system on which is installed Xubuntu 16.04 LTS on the entire disk. 
It works well but I would like to install xubuntu on an external ssd drive too, which allows in booting on to have much more place...

I have tried to install Xubuntu with the option install something else : 

I booted on the Xubuntu live USB
Lunched Gparted to prepare the external SSD with partition : fat32 (with flag boot and esp for the EFI) , ext4 and swap-linux.
Ran the Xubuntu installer, after the step where I chose install something else. The partitioner showed me the MMC (with partitions efi, ext4->xubuntu 16.04 and swap) and SSD with the right partitions (efi, ext4, swap). 
I selected ext4 partition and chose the mounting point / and formating.

I clicked on install but a window appeared which prevented me that the system would format ext4 partition as ext4, swap as swap from ssd AND ALL MY MMC AS SWAP... I don't understand why the system want to format my MMC whereas i didn't tick the box neither nothing else...

I really need your help !!! Thanks you very much...

---

### Post by Dennis N on 2016-11-01
The installer always reports it is going to format the swap partition whether you ask it to or not. If you have another swap partition on the internal drive, it will format that swap partition too, but certainly it should not format all of the drive. You may have misread it - check again what that message says. Actually, you don't need a second swap on the external drive - _one_ available swap partition (even on a different drive) is enough.

---

### Post by sebastien95 on 2016-11-02
Thank you for your help Dennis N !

I agree with you but i have doubts about the system message. I will take a picture and ask you a verification please ;)

Bye !

---

### Post by Dennis N on 2016-11-02
> I will take a picture...
Good idea. You can take screenshots from the Live CD during the installation process. Save each one to the Desktop, and before exiting the live CD, copy them all to a 2nd USB stick (not the installer) or else they will be lost.

---

### Post by sebastien95 on 2016-11-03
It's good for my installation. I trusted you and I finally clicked on continue because I really think as you about the system message and what will be formated.

So just the swap partition has been formatted on my MMC, I chose bootloader on MMC to allow booting without the external SSD.

Thank you very much Dennis ! ;)

Just another question : if I had chose Erase entire disk and I had selected the external SSD, would the bootloader have always been on the MMC ? And if it had not, could I have changed this ?

---

### Post by Dennis N on 2016-11-03
> Just another question : if I had chose Erase entire disk and I had selected the external SSD, would the bootloader have always been on the MMC ? And if it had not, could I have changed this ?


If you install as UEFI, even if you specify your disk sdb for the bootloader location, it is still installed to the EFI system partition on the first hard drive - sda.

This is how the Ubuntu installer (called ubiquity) does things in UEFI mode. Other distros, like Fedora or Arch, allow you to install to any EFI system partition you have on your internal drives.

However, in BIOS mode you can install bootloader to the 2nd drive.

---

### Post by sebastien95 on 2016-11-05
Okay Dennis thank you very much for your help ! :)

---

