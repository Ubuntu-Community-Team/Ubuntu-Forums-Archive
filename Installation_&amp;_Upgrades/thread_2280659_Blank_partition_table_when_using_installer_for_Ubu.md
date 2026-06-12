---
title: "Blank partition table when using installer for Ubuntu 15"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by GUnot2100 on 2015-06-01
So I was going to dual boot install Ubuntu next to my existing Windows 8.1 system. I already have the unallocated partition I want to install it in. I can boot into Ubuntu from my flash drive fine. But when I go to install it, firstly it doesn't give me an option to install it fully on my hard drive or that "something else" option, it goes straight to the partition view window in which it shows no partitions at all so I can't select the unallocated space I want to install it in. My best guess is that this is due to my system using GPT drives and UEFI, because this process was really simple on a laptop I had several years ago. I've searched and I can't find anything that I could do to make it work. My computer is a Toshiba Satellite E45t-A4300. Is there anything I can do? &#65279;Some people have mentioned that I may not be booting from the flash drive in UEFI mode. I never had any experience with these new types of drives and firmware so I have no idea where to go from here. I used Rufus to flash the iso on my flash drive with the option to use GPT and UEFI mode, if that helps.

---

### Post by oldfred on 2015-06-01
Have you turned off Windows fast startup or always on hibernation. And if UEFI has fast boot, turn that off also, or you may have issues getting into UEFI.
Often better to have secure boot off, but not required. Grub will not dual boot Windows from grub menu with secure boot on, but you can dual boot from UEFI menu.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support) 
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Even more links & info in link in my signature.

---

### Post by GUnot2100 on 2015-06-01
> **oldfred said:**
> Have you turned off Windows fast startup or always on hibernation. And if UEFI has fast boot, turn that off also, or you may have issues getting into UEFI.
Often better to have secure boot off, but not required. Grub will not dual boot Windows from grub menu with secure boot on, but you can dual boot from UEFI menu.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support) 
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

Even more links & info in link in my signature.
Windows fast startup is disabled, fast boot is disabled, secure boot has been turned off since I started attempting to install it. I now realize that I won't be getting the "Installation type" screen with the installer so that can be disregarded.
I was told to use this command to list my drives, or partitions that Ubuntu can see:
```
ls -l /dev/sd*&#65279;
```
which does show all my partitions in terminal.
Also this one to confirm that Ubuntu is booting in UEFI mode:
```
ls -l /sys/firmware/efi
```
and it appears it is so I might have to go more in depth into those links.

---

