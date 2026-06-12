---
title: "install lubuntu 20.04 (currently using 18.04.4 dual boot with windows 10 )"
date: 2020-05-18
forum: Installation &amp; Upgrades
---

### Post by alanlinux on 2020-05-18
Hello,

I've been using lubuntu 18.04.4 on X1 Carbon (7th gen), and would like to install lubuntu 20.04. But I'd like to keep my current setting for the dual boot with Windows 10 (currently using GRUB 2.02-2ubuntu8.15). Also, currently, I ahve 

What should I pay attention to during the installation? Are there any "do's" and "don'ts" that I should bear in mind?

Thanks in advance!

---

### Post by oldfred on 2020-05-18
Have you updated UEFI? And if SSD, firmware for SSD?
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

If installs are UEFI, you need to install in UEFI boot mode.
And must have good backups.
Backups should include /home, list of installed apps to make it easy to reinstall, any server type apps & data that may be in / (root), and any systemwide custom settings you may have done in /etc. I edit several grub files and just copy those into /home so my backup of /home includes those.

Standard install, if in same boot mode as Windows, will add Windows to grub boot menu.
But Windows fast start up or hibernation must be off for Linux NTFS driver to see it. Note that Windows updates will turn it back on, so double check before reinstalling.

I prefer to install to 25 or 30GB / (root) partition and have all data in separate partition. So I still have 16.04, 18.04., 20.04 and maybe some more installs just to test some changes where I do not want default settings in /home changed. But have same data in all my installs.

---

### Post by alanlinux on 2020-05-21
Thank you! I just did it last night and it worked. During the installation, the instructions asked me to create a partition for /boot/efi and flag it as ESP. I did that and I couldn't find the ESP option in the pulldown menu and just chose "boot" as the flag. I also created a /swap partition.

It's all good and the microphone now works (it didn't on 18.04.4 on X1 Carbon Gen 7), but I'm still trying to get used to the Qt desktop. I missed the hotkeys to "snap" app windows to left/right side of the monitor...

---

