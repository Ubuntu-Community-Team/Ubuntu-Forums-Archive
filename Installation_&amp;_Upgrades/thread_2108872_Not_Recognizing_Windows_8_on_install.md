---
title: "Not Recognizing Windows 8 on install"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by PeterSchuelke on 2013-01-25
Hey I've been all over this forum the last day and found some useful information. But I'm still stuck installing Ubuntu next to Windows 8.

So here's the details:
Bought a brand new Samsung NP365e5c running Windows 8.
I've made a LiveDVD of Ubuntu 12.10 64bit.
I've followed the instructions from [here]("https://help.ubuntu.com/community/UEFI"). And I've tried the suggestions from [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system") and [here]("http://askubuntu.com/questions/227152/cannot-detect-windows-8-from-ubuntu-12-04-live-usb-installation-on-toshiba-qosmi")

So here's what I've done. Before starting I insert my dvd. Power up and press F2, where I get the bios screen. Under the boot menu I get: Boot Device Priority, Touch Pad Mouse and Secure boot. The first round I change the 'Boot Device Priority'. Here I actually on got one option which was 'Window Boot Manager'. I disable it, hit F10 and restart. The computer then boots to the DVD, which I select 'Try Ubuntu'. I went through the installation and poked around the OS for a bit and got no 'secureboot' or 'signature' errors. So I exit out and restart, this time I select "Install Ubuntu' and let it do it's thing. When it gets to the installation type I don't get the option to install along side Windows. 

So I exit out and restart hit F2 to enter the bios. Back to the boot menu i disable the 'Secure Boot' which then produces another menu option 'OS Mode Selection.' It has the options: UEFI OS, CSM OS and 'UEFI and Legacy OS'. I've tried both 'UEFI OS' and "UEFI and Legacy OS' Both options will boot Windows just fine, but the Ubuntu install won't recognize windows. I've also tried all these options with a manually made partition using windows. I also know I am getting into EFI mode with Ubuntu.

Note: I do have a Ubuntu 12.10 32bit dics made as well. It can detect windows and gives the option to install next to it.

Thanks for you help in advance.

---

### Post by carusoswi on 2013-01-25
> **PeterSchuelke said:**
> Hey I've been all over this forum the last day and found some useful information. But I'm still stuck installing Ubuntu next to Windows 8.

So here's the details:
Bought a brand new Samsung NP365e5c running Windows 8.
I've made a LiveDVD of Ubuntu 12.10 64bit.
I've followed the instructions from [here]("https://help.ubuntu.com/community/UEFI"). And I've tried the suggestions from [here]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system") and [here]("http://askubuntu.com/questions/227152/cannot-detect-windows-8-from-ubuntu-12-04-live-usb-installation-on-toshiba-qosmi")

So here's what I've done. Before starting I insert my dvd. Power up and press F2, where I get the bios screen. Under the boot menu I get: Boot Device Priority, Touch Pad Mouse and Secure boot. The first round I change the 'Boot Device Priority'. Here I actually on got one option which was 'Window Boot Manager'. I disable it, hit F10 and restart. The computer then boots to the DVD, which I select 'Try Ubuntu'. I went through the installation and poked around the OS for a bit and got no 'secureboot' or 'signature' errors. So I exit out and restart, this time I select "Install Ubuntu' and let it do it's thing. When it gets to the installation type I don't get the option to install along side Windows. 

So I exit out and restart hit F2 to enter the bios. Back to the boot menu i disable the 'Secure Boot' which then produces another menu option 'OS Mode Selection.' It has the options: UEFI OS, CSM OS and 'UEFI and Legacy OS'. I've tried both 'UEFI OS' and "UEFI and Legacy OS' Both options will boot Windows just fine, but the Ubuntu install won't recognize windows. I've also tried all these options with a manually made partition using windows. I also know I am getting into EFI mode with Ubuntu.

Note: I do have a Ubuntu 12.10 32bit dics made as well. It can detect windows and gives the option to install next to it.

Thanks for you help in advance.

Mine is an NP700Z5Z from Samsung. Same problem.  I tried first installing to the C drive after using Windows disk management to shrink the windows partition.

I expanded the windows partition back to its original size, and shrank the partition on the second hard drive.

Still no go as the live cd does not acknowledge the presence of Windows on the computer.

I just got this computer back from Samsung's service provider after corrupting the Windows disc image in my first attempt to setup a dual boot.  In that case, Ubuntu recognized the Windows OS, but a corrupted Live CD would proceed to finish the installation, but you could not boot into Ubuntu.

On my last try, I managed to hit the wrong choice and selected for Ubuntu to take u the entire disc.  Then I stopped the install, tried to run the Windows restore, but it was too late.  To add insult to injury, whatever bit of hard coding allows one to eject the CD on this machine also would not function, so I could not get the restore disc out of the machine.  Otherwise, I would have gone ahead and installed Ubuntu on the entire disc or used the live cd to repartition, whatever.

Anyhow, I am determined not to mess the windows partition up again, so I don't want to take a leap of faith and install Ubuntu when it is not recognizing that Windows OS.

Suggestions would be appreciated.

Caruso

---

