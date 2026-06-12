---
title: "Trouble with efi-booting on mac"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by xenumason on 2012-12-29
Hi 
I'm trying to dualboot osx and ubuntu 12.10 on my macbook. I'm setting up efi-booting following this tutorial: [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

I'm up to point 26. Basicly I've installed everything but grub2. The sudo grub-install command doesn't work for me. The only thing I'm doing different than the tutorial is that I'm installing 12.10 instead of 12.04. When I type the grub-install command I get "Install device isn't specified" although I typed sudo mount /dev/sda1 /boot/efi

If I try sudo grub-install /boot/efi I get "usr/sbin/grub-bios-setup: Not found"

the command: ls /boot/efi/efi/ubuntu gives me grubx64.efi but the boot.efi is missing.

Do any of you have any suggestions how to proceed?

---

### Post by daInvincibleGama on 2013-01-02
I'm having the same issue.(I followed that guide.)

It is my understanding so far that grub does not want to install grub-efi unless it was booted from EFI, or some such.

I tried the instructions here
[https://wiki.archlinux.org/index.php/GRUB2#UEFI_systems_2](https://wiki.archlinux.org/index.php/GRUB2#UEFI_systems_2)
which got me to grub2 efi in the EFI system partition, but no grub.cfg generated.

I also tried to use this:
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)

but that errored out because of the same reason. It gets to grub-install, then errors out. :(

So I'm stumped as well. If you figure anything out, please let me know.

---

### Post by grahammechanical on 2013-01-02
I am not saying that this is the solution. I have standard BIOS on my machine. I cannot say that I have tested this on UEFI but I thought that the command was

```
sudo grub-install /dev/sda
```

Change sda to sdb, etc., if you do not want grub installed into the first hard disk (sda). when I leave off the /dev/sda bit I get the  "Install device isn't specified" error.

for anyone following this thread, there is also these links

[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

regards.

---

### Post by shrubz on 2013-01-04
> **xenumason said:**
> Hi 
I'm trying to dualboot osx and ubuntu 12.10 on my macbook. I'm setting up efi-booting following this tutorial: [http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

I'm up to point 26. Basicly I've installed everything but grub2. The sudo grub-install command doesn't work for me. The only thing I'm doing different than the tutorial is that I'm installing 12.10 instead of 12.04. When I type the grub-install command I get "Install device isn't specified" although I typed sudo mount /dev/sda1 /boot/efi

If I try sudo grub-install /boot/efi I get "usr/sbin/grub-bios-setup: Not found"

the command: ls /boot/efi/efi/ubuntu gives me grubx64.efi but the boot.efi is missing.

Do any of you have any suggestions how to proceed?

I am having the exact same problem following the same guide. Did you install from "Windows" disk or "EFI Boot" from Mac boot menu?

I have been in contact with the author and have received some help, but this has not helped me. Would you like me to post his replies here?

---

### Post by shrubz on 2013-01-07
Finally got it to work by following these instructions from the above post

> Converting Ubuntu into EFI mode
Start Boot-Repair, click on "Advanced options", go to the "GRUB location" tab.

If you do not see a "Separate /boot/efi partition" line, this means that your PC does not have any EFI partition. In this case, exit Boot-Repair, then create an EFI partition (see the "Creating an EFI partition" paragraph above).
**If you see a "Separate /boot/efi partition" line, tick it then click the "Apply" button**.

This enabled me to boot Ubuntu from rEFInd, however then I have massive problems with Nvidia Drivers for my graphics card, not letting me boot into X once I installed Proprietary Drivers. I followed the instruction below, available at this [page.]("http://blog.projectz.me/2012/10/21/setting-up-ubuntu-12-10-on-a-macbook-pro/")

> **Fixing the login issue**

Turns out there may be a bug in the NVidia install DEB’s on 12.10 which calls  linux-headers-generic but doesn’t install them, so while the package tries to install it actually fails. To get round this you need o do the following from the command line:

**sudo apt-get install linux-headers-generic**

Once the headers have installed, you need to reconfigure the Nvidia drivers which will depend on which one you chose when you installed them.

[B]This if you have nvidia-current (proprietary,tested)

sudo dpkg-reconfigure nvidia-current[/B]

[B]This if you have nvidia-current-updates (proprietary)

sudo dpkg-reconfigure nvidia-current-updates[/B]

[B]This if you have nvidia-experimental-304 (proprietary)

sudo dpkg-reconfigure nvidia-experimental-304[/B]

A reboot will then resolve this login issue and display Unity 

However this just made Unity freeze after a few minutes, so i gave up.

I booted back into mac reformatted all Linux partions as one FAT Partition, then used Bootcamp to restore my Disk to 1 Partition (surprised that worked).

Used Gparted live CD to edit my EFI and remove all non APPLE entries.

Back to Stock for now!!

---

