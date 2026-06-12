---
title: "Is there a way to make and ues a boot partion on install for a dual boot windo setup?"
date: 2024-04-28
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2024-04-28
Is there a way to make and ues a boot partion on install for a dual boot windo setup? Or would I have to set this up after installing Ubuntu?

---

### Post by oldfred on 2024-04-28
Not sure what you mean?

You have /boot, which is not required for most desktops, but is used with servers & LVM when full drive encryption is specified. Full drive encryption means not dual boot, although more difficult to configure as dual boot as not a default install.

You have an ESP - efi system partition which has boot,esp flags for UEFI boot. Normally all systems on a drive share one ESP.

Or you have / (root) the operating system.

---

### Post by Omnios on 2024-04-28
> **oldfred said:**
> Not sure what you mean?

You have /boot, which is not required for most desktops, but is used with servers & LVM when full drive encryption is specified. Full drive encryption means not dual boot, although more difficult to configure as dual boot as not a default install.

You have an ESP - efi system partition which has boot,esp flags for UEFI boot. Normally all systems on a drive share one ESP.

Or you have / (root) the operating system.

Thanks for the reply. I have not used Linux for a while and a long time ago I remember you could put /boot and grub in its own partition so grub still works if your Linux install is borked or deleted and still log in with grub. Not sure exactly how that worked.

---

### Post by oldfred on 2024-04-28
That sounds more like what I did back before grub2. And grub2 became the standard in 2010.
Systems since 2012 are UEFI, and UEFI boot is different than the old BIOS boot, also.

Best just to keep live installer with current version of Ubuntu that you have installed as a repair disk. And always have good backups.

---

### Post by grahammechanical on 2024-04-29
I shall assume that Windows is already on the machine; and you know how to download and burn to a USB memory stick Ubuntu 24.04 LTS ISO image. I also assume that you know how to boot from the USB memory stick using the UEFI settings utility.

When the Ubuntu 24.04 LTS ISO image loads you will see a boot menu. At the top it will say

> Try or Install Ubuntu

Select that option and the ISO image will load to a desktop. You will then see a white panel that says 

> Processing Ubuntu

After a little while you will get some pages giving various options. After those options are selected you will be able to choose Try Ubuntu or Install Ubuntu.

Then you will be offered 

> Interactive Installation
For users who want to be guided step by step through the installation

Or

> Automated Installation
For advanced users who have an autoinstall yaml for consistent and repeatable system setups 

When we choose Interactive Installation we get offered a Default selection - just the essentials, web browser and basic utilities or Extended selection. (This is the usual Ubuntu Desktop)

After accepting or refusing the installation of proprietary software we then get offered:

> How do you want to install Ubuntu?
Install Alongside them
Erase Disk and install Ubuntu
Manual Installation

Whether we choose Install Alongside or Manual Installation the Ubuntu installer will recognise the existence of Windows and produce a Boot menu (called Grub) that will give options to choose from whatever operating systems are installed on the machine.

With the Erase Disk and Install Ubuntu option we only get one operating system on the machine (Ubuntu) and although there still is a Grub boot menu it will not normally appear .

I hope this is what you are looking for. If not, then I do not understand what it is that you are asking.

Regards

---

