---
title: "Can't install Ubunut or Try it without installing"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by pedropcruz on 2020-03-07
Hello guys! I am new here so if anything is wrong, please delete this post or move it.

But I have recently bought my Desktop PC with this specs:

MSI B450 TOMAHAWK MAX ATX AM4 Motherboard
AMD Ryzen 9 3900X 3.8GHz AM4 BOX
G.Skill Kit 32GB (2 x 16GB) DDR4 3200MHz Ripjaws V Black CL16
Kingston A2000 1 TB M.2-2280 NVME Solid State Drive
GeForce RTX 2070 
SuperSeaSonic FOCUS Plus Gold 650 W 80+ Gold Certified Fully-Modular ATX Power Supply
Western Digital Black 4 TB 3.5" 7200RPM Internal Hard Drive
ASUS PCE-AC55BT WLAN
Cooler CPU Noctua NH-U12S

Already have disabled UEFI secure boot on BIOS as well, and nothing works... I really need help on this, because this computer it's for work.

I have download a thousand times a new ISO, put on a pen with Rufus/unetbootin and nothing works.

Many thanks

Pedro Cruz

---

### Post by yancek on 2020-03-07
You're not likely to get help with statements such as "nothing works".  You need to provide specifics which you have done with regard to your hardware so, did you download the iso (this is some version of Ubuntu, correct?) from the official site?
Did you verify that the actual download worked by doing an md5checksum or sha256 checksum?  Why did you disable UEFI?  According to the information you posted, this is a new machine with NO operating system on it?  When you go to the BIOS firmware, do you see Boot Options to select the drive you want to boot from, generally shown by the name of the manufacturer.  You need to be more specific on exactly what happens when you try or you will be unlikely to get any response.

---

### Post by pedropcruz on 2020-03-07
Sorry @yancek , i can provide any info you want :) . 

And i tried with Ubuntu 18.04 LTS and 19.01 and them have the same problem. Sometimes i can get into the loading screen (only seeing the Ubuntu logo) and if i try again, sometimes i enter to the system, i move the mouse only and it freezes and PC restarts.

I disable UEFI because it was the result of my search, i checked some people with the same problem, but it seems its not the same reason i guess...

The operating system its hard to install, but I did it and have a Windows 10, but want to put a dual boot with Ubuntu.

Can You share how i can make md5checksum or sha256 checksum ?

And sorry for not posting well.

Many thanks

---

### Post by yancek on 2020-03-08
Verifying downloads is explained at the Ubuntu site below.

[https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview)

If you have windows 10 installed and it was installed and came with the computer, it is almost certainly installed in UEFI mode.  If that is the case, then you must install Ubuntu UEFI or you will have problems booting.  The Ubuntu documentation at the site below explains the reasons for that and also has a detailed explanation of how to dual boot uefi with windows 10.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You have  NVidia graphics which sometimes is a problem so when you boot the Ubuntu usb, when you see the menu with the Ubuntu option, hit the e key on the keyboard and you will get a new screen with the menuentry showing.  Use the arrow keys on your keyboard to go down to the line which  begins with the word 'linux' and then use the right arrow key to go to the end of that line where it shows quiet splash and replace that with nomodeset.  Then use the key combination shown at the bottom of that screen to continue booting.  See if the results are better.

---

### Post by ubfan1 on 2020-03-08
Check the vendor for BIOs/firmware updates first.  You might limp by with acpi=0, but with possibly drastic issues like seeing only one cpu core.

---

### Post by pedropcruz on 2020-03-10
> **yancek said:**
> Verifying downloads is explained at the Ubuntu site below.

[https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview)



I already have done this, and it's all good, they give me OK :) (I check on Windows, not on Ubuntu, but the values are the same so everything works)

But this computer was made by me, so he didn't come with Windows by default. But on my BIOS I have the UEFI + Legacy, but that's not a problem right?

I didn't understand well the thing "install Ubuntu on UEFI Mode" to be honest. Because it recognizes the pen, but it only freezes sometimes.

---

### Post by CelticWarrior on 2020-03-10
> **pedropcruz said:**
> But on my BIOS I have the UEFI + Legacy, but that's not a problem right?

Could be...
From the beginning: You have UEFI, you don't have BIOS. Legacy or CSM is what "emulates" the old BIOS. However, Legacy mode is not an option for you considering the hardware.
So, it follows that it should have "UEFI only" in order to avoid mistakes. A typical live Ubuntu USB is capable of booting either way and having "UEFI+Legacy" set result in seeing two entries for the same USB, one with UEFI in the name and the other without and you may choose the wrong one. "UEFI only" assures boot and installation in UEFI mode.

> Because it recognizes the pen, but it only freezes sometimes.
The reason and workaround already explained in post #4. You need to use an additional parameter - nomodeset - as instructed, to boot the live session and install. Also you need the newest you can find and that means 19.10 or even the soon to be released 20.04 (April). Make sure to select also disable Secure Boot and, during installation, select the option to install third-party drivers that now installs the Nvidia proprietary drivers that you need for the graphics. Hopefully no other action will be needed after installation.

---

### Post by P-I H on 2020-03-10
The best is to install both W10 and Ubuntu in UEFI mode. You have to disable "Fast Boot" and "Secure boot" in BIOS. I recommend to Boot only in UEFI mode.
To mix UEFI mode and Legacy mode create problems as the Ubuntu loader always tries to store the  to boot files on the first disk either nvme0n1 or sda. Incase of a dual boot with W10 this is no problem in UEFI mode as the boot files are stored in the same ESP (EFI System Partition).
I use a older MSI B350 Tomahawk motherboard on this computer. On my motherboard you have to use a specific USB port for the USB boot device. It's one of the USB 2.0 Type -A ports besides the PS/2 combo keyboard/mouse port on the Back Panel. To boot you have to select UEFI USB..... in BIOS.
Information in this post might help
[https://ubuntuforums.org/showthread.php?t=2436617](https://ubuntuforums.org/showthread.php?t=2436617)
In case you are going to use the nvme disk for both W10 and Ubuntu you have to create the space for Ubuntu. See this tutorial
[https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

As you have an Nvidia GPU you probably have to set "nomodeset" as mentioned above.

---

### Post by CelticWarrior on 2020-03-10
> To mix UEFI mode and Legacy mode create problems as the Ubuntu loader  always tries to store the  to boot files on the first disk either  nvme0n1 or sda.

With NVME drives Legacy is NOT even an option.

---

### Post by u666sa on 2020-03-13
I’m thinking it’s video problem, I’m not sure hiw it’s done in ubuntu, in fedora you have to add nomodeset to linux from grub e key. Give it a go

---

### Post by pedropcruz on 2020-03-14
> **CelticWarrior said:**
> Could be...
From the beginning: You have UEFI, you don't have BIOS. Legacy or CSM is what "emulates" the old BIOS. However, Legacy mode is not an option for you considering the hardware.
So, it follows that it should have "UEFI only" in order to avoid mistakes. A typical live Ubuntu USB is capable of booting either way and having "UEFI+Legacy" set result in seeing two entries for the same USB, one with UEFI in the name and the other without and you may choose the wrong one. "UEFI only" assures boot and installation in UEFI mode.


The reason and workaround already explained in post #4. You need to use an additional parameter - nomodeset - as instructed, to boot the live session and install. Also you need the newest you can find and that means 19.10 or even the soon to be released 20.04 (April). Make sure to select also disable Secure Boot and, during installation, select the option to install third-party drivers that now installs the Nvidia proprietary drivers that you need for the graphics. Hopefully no other action will be needed after installation.

Well, I'm not bringing good news...

its already on UEFI mode, I put already the nomodeset option as well, but for some reason this continues to freezing after some seconds. But the good new its with the nomodeset, that disable the good graphics.

More opinions/options ?

Many thanks and sorry for long delay

---

