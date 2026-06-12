---
title: "Boot Problems - Ubuntu 24.04 LTS"
date: 2024-05-17
forum: Installation &amp; Upgrades
---

### Post by sebastianbing on 2024-05-17
HI Ubuntu Experts!

I was trying to install the operation system Ubuntu 24.04 LTS on my laptop.

First of all I was creating a Live USB via Windows/Rufus. Afterwards, I was able to boot from the USB stick and also the installation went without any problems.

Anyhow after the installation no OS is listed in the Boot section of the BIOS. Assuming that i am facing boot problems, I was installing & opening the programm Boot-repair and was creating a boot info summary that I would like to share with you guys here:
[https://paste.ubuntu.com/p/67dy5VBNmp/](https://paste.ubuntu.com/p/67dy5VBNmp/)

I've got a 128 GB SSD Device Path /dev/nvme0n1 where i want to install Ubuntu 24.04 LTS.

Please let me know if you need some more information.

Thanks in advance!
Have a nice weekend!
Sebastian

---

### Post by oldfred on 2024-05-17
Was this intentional on your part? Install is also in BIOS boot mode.
> The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

Microsoft has required UEFI/gpt since 2012, so almost all hardware is UEFI. And old (very old) BIOS install was allowed only as some major users of Windows wanted newer software on older systems in 2012.
Many new laptops starting in 2020 are now UEFI only.

Your sda looks unpartitioned with no formatted partitions.
Your sdb is the live installer.

You show you also have nVidia.
Did you choose to install the optional, restricted drivers to get the correct nVidia driver installed as part of install.

While if new install, probably better to totally reinstall in UEFI boot mode and be sure to install proprietary drivers, you can press shift key while starting to boot to get grub menu.
Grub menu does not show automatically if only one install. In UEFI boot mode, you use escape key to get menu, not shift key.

At grub menu is a recovery mode menu. Turn on Internet & using terminal you can install the nVidia driver.
First make sure system is updated.
sudo apt update
sudo apt full-upgrade
It used to be this, but recently have seen other commands, not sure if that was also Ubuntu or not.
# list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 
sudo ubuntu-drivers autoinstall

If a driver already installed an you change, you must purge first as new driver does not uninstall old driver & you get conflicts, or more problems.

Server instructions, but should be the same for desktop.
[https://ubuntu.com/server/docs/nvidia-drivers-installation](https://ubuntu.com/server/docs/nvidia-drivers-installation)

---

### Post by sebastianbing on 2024-05-18
Hi oldfred! Thank you for all the information. I will have a closer look the next days and come back to you afterwards. &#128077; Seb

---

### Post by sebastianbing on 2024-05-23
Hey everyone!

Problem solved! The golden keys are 'UEFI Boot Stick' and the 'Shift key'.

Thank you @oldfred for you big assist! I appreciate that!

It was about time to find out the difference between UEFI and BIOS. :P I created another UEFI Boot stick with GPT as the Patition table via Windows/Rufus.
And it worked out! But only on 1 condition! It was absolutely necessary to press the shift key in order to enter the grub menu and start the installation of Ubunut from here. So the shift key was another very good hint!
I was also checking the 'third party packages' during the installation of ubuntu to be sure to get the latest nvidia drivers.

Bye for now ;)

Seb

---

