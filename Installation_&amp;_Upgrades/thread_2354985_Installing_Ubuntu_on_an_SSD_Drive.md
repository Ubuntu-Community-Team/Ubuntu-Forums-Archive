---
title: "Installing Ubuntu on an SSD Drive?"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by dannyk2 on 2017-03-08
My new desktop has a 250GB SSD drive. Could someone tell me how i might install the latest version of Ubuntu on it please. I don't want to partition the drive. As Ubuntu will be my default OS i want to keep the drive just for Ubuntu. Hope you can understand me lol. Thanks

---

### Post by oldfred on 2017-03-08
SSD is no different than HDD, other than perhaps a few configuration settings after you install.

You must partition.
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 


Is system UEFI then use gpt partitioning and boot installer in UEFI boot mode.
I usually add both the ESP - efi system partition for UEFI boot and the bios_grub for BIOS boot, but only one or the other is required.

What brand/model system?

You can follow the many threads on dual booting, but skip all the issues with Windows.
With UEFI, the default install includes the ESP, / (root) & swap.
Many like separate /home and/or data partitions(s), best then to partition in advance with gparted and use Something Else install option.
       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
Did system come with Windows? If so best to fully back that up. Many make leap to Linux and later find that one application that only runs on Windows and then want to dual boot.

---

### Post by SuperFreak on 2017-03-08
Download Ubuntu iso [HERE]("https://www.ubuntu.com/download/desktop").Create LiveUSB or LiveDVD of chosen Ubuntu version following instructions [HERE]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") or [HERE]("https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu"). Insert Live USB or DVD and reboot. Immediately go into BIOS or UEFI (usually pressing Del Key or Esc key or F1,F2 or F3 depending on make model of PC). Now go into boot order and ensure that PC boots to USB or DVD first (in UEFI mode if available). Now Save and Exit BIOS settings. You should now be booting into a Live version of Ubuntu. Check out the features and decide if you really want Ubuntu. If you do click on Install Ubuntu from desktop. The on screen dialogue should guide you through the procedure (further instructions [HERE]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick"))
It should be noted that you need to select the correct iso of Ubuntu. There are 32 and 64 bit editions (you probably want 64bit if the computer is 6 years old or newer) and there are different flavours of ubuntu such as Xubuntu, Lubuntu (for low powered PCs), Kubuntu etc

I have omited how to make a LIve DVD as few people use optical drives but if that is the way you need to go just google it

---

### Post by dannyk2 on 2017-03-08
I'd just like to say a very big thank you, to the both of you, for taking the timeout to help an old geriatric Ubuntu user like myself.

---

