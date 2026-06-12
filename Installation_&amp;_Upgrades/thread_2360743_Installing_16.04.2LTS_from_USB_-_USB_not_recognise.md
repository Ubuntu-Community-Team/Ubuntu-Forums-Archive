---
title: "Installing 16.04.2LTS from USB - USB not recognised as boot option"
date: 2017-05-08
forum: Installation &amp; Upgrades
---

### Post by hril230 on 2017-05-08
Hello

I'm running Windows 10 on an HP Envy laptop and am trying to install Ubuntu16.04 as a dual-boot alongside Windows.
I already have Ubuntu14.04 installed but that operating system is broken and seems unfixable so I want to reinstall. I'm hoping to just overwrite it with a new 16.04 install.
I used Rufus to burn the Ubuntu16.04 IOS to a USB drive.
However, when I restart my computer and select the 'boot from USB' option I get an error message saying 'the boot device did not work'.

I've tried this with Universal-USB-Installer instead of Rufus, I've tried it with GPT and MBD partition types, I've tried it with a Kingston2.0 USB and an Apacer 3.1 USB, I've tried it with a 14.04 IOS instead of 16.04, I've tried it with Boot Security disabled and I've tried it with Legacy Configuration enabled.
Nothing works.

I need an Ubuntu OS running on my laptop for a University project. Please help.

---

### Post by yancek on 2017-05-08
windows 10 is generally installed using UEFI/GPT if pre-installed.  If it is then you need Ubuntu installed UEFI/GPT or you will have problems.  Take a look at the Ubuntu documentation at the site below which explains it and how you can install correctly.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you can't boot from usb, can you use a DVD?  Have you tried the flash drives on another computer to see if they boot?  I think you might need to investigate the BIOS boot priority to see if there are other options which will enable you to boot the usb.  Often the device will be listed under hard drives by the name of the manufacturer.

---

