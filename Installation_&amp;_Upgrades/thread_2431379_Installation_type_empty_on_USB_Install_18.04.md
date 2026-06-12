---
title: "Installation type empty on USB Install 18.04"
date: 2019-11-15
forum: Installation &amp; Upgrades
---

### Post by hcphoon01 on 2019-11-15
[COLOR=#242729][FONT=Arial]I am trying to install ubuntu on a USB but when I boot to it and attempt an install the installation types menu is empty and I cannot add a partition to install to as the installer freezes.[/FONT][/COLOR]

---

### Post by QIII on 2019-11-15
Moved to Installation and Upgrades for a better fit.

---

### Post by oldfred on 2019-11-15
UEFI or BIOS install?

Installing from one USB flash drive as live installer to empty USB flash drive to be full install?

Either way best to partition in advance & if UEFI, you must have ESP on flash drive. Ubiquity installer will not correctly install grub to flash drive, but will normally install it to first ESP (assuming you have one).
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

---

### Post by hcphoon01 on 2019-11-15
> **oldfred said:**
> UEFI or BIOS install?

Installing from one USB flash drive as live installer to empty USB flash drive to be full install?

Either way best to partition in advance & if UEFI, you must have ESP on flash drive. Ubiquity installer will not correctly install grub to flash drive, but will normally install it to first ESP (assuming you have one).
Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)

Sorry I'm not sure what you mean, I followed this tutorial [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0) if that is any help

---

### Post by yancek on 2019-11-15
The link you posted simply explains how to use the software 'rufus' to create a bootable usb of Ubuntu.  Have you completed that part successfully and now you are booting the computer with the Ubuntu usb?  Since the instructions assume using windows, which release of windows are you using?  If you have windows 8 or 10, it hibernates by default and that has to be turned off in the BIOS firmware and on windows or a Linux installer will not mount these partitionss and so you cannnot use them.  Not sure this is the problem but it's a place to start.

---

### Post by oldfred on 2019-11-15
If newer UEFI system, on USB selection screen be sure to select gpt & UEFI.
The MBR & BIOS is only for the old BIOS boot. 
While Ubuntu ISO is for both UEFI and BIOS, it seems Rufus only makes installer one or the other.

---

### Post by hcphoon01 on 2019-11-16
> **yancek said:**
> The link you posted simply explains how to use the software 'rufus' to create a bootable usb of Ubuntu. Have you completed that part successfully and now you are booting the computer with the Ubuntu usb? Since the instructions assume using windows, which release of windows are you using? If you have windows 8 or 10, it hibernates by default and that has to be turned off in the BIOS firmware and on windows or a Linux installer will not mount these partitionss and so you cannnot use them. Not sure this is the problem but it's a place to start.

Im using Windows 10 so that hibernation might be a thing, where in the BIOS would I turn that off?

> **oldfred said:**
> If newer UEFI system, on USB selection screen be sure to select gpt & UEFI.
The MBR & BIOS is only for the old BIOS boot. 
While Ubuntu ISO is for both UEFI and BIOS, it seems Rufus only makes installer one or the other.

I tried using GPT and UEFI but now it doesnt show up in the BIOS to be able to boot to

---

### Post by yancek on 2019-11-16
The link below explains how to turn off fastboot in windows and gives a pretty detailed explanation of its use.

[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

You haven't indicated what hardware you have and BIOS firmware options vary a good deal for computer manufacturers.  Access the BIOS firmware and explore it but if you don't understand something, don't change it.  If you post specifics on the computer you are using such as the manufacturer and model, someone here may help.  You might also do an online search for information on disabling hibernation on your model.

---

