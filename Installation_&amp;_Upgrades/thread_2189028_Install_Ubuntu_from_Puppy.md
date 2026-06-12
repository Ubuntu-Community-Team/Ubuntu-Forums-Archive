---
title: "Install Ubuntu from Puppy"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by alistair_gower-j on 2013-11-20
Hi,
I'm looking to install Ubuntu (preferably 13.10) onto my hard drive and I'm currently running off Puppy Linux OS. I am unable to boot my Windows 7 operating system so am running off puppy which I have installed onto a partition on my hard drive and looking for a more user friendly system. I have created a separate partition in extf3 format ready for Ubuntu to be installed onto but am unsure of how to proceed. I would prefer not to spend money on cd's as I am a fairly poor student and currently only own a 1gb flash drive (my 16gb one has been made unusable by a friend). I am a bit of a novice with computers so simple easy to follow steps are preferable.

Thanks

---

### Post by sudodus on 2013-11-20
Welcome to the Ubuntu Forums :-)

Specify your computer and what you intend to do with the computer! It makes it much easier to give relevant advice. I'm not sure that standard Ubuntu would be the right choice for you.

- Computer brand name, model, cpu, ram (size), graphics card
- Typical tasks or software that you want to run in the computer
- Do you intend to have dual boot with Puppy or should there be a single operating system?

-o-

It is possible to make a boot USB drive of a 1 GB pendrive with several tools. I think ***Unetbootin*** or ***mkusb*** are fairly easy to use and have a good record (high chance to succeed). See these links

Unetbootin and other tools:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

mkusb:
[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

-o-

It might be possible to wipe the first megabyte of the damaged 16GB pendrive with mkusb and after that make a new partition table with ***gparted*** (probably possible to do in Puppy but I have not tried that myself).

---

### Post by grahammechanical on 2013-11-20
I have never tried this and it will not work on your system unless Puppy Linux uses Grub 2 and not Grub legacy.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

> [COLOR=#333333][FONT=Ubuntu]Ubuntu ISOs are designed to allow booting directly from the hard drive using GRUB 2 and eliminates the need for burning a CD/DVD. This feature permits the user to boot and use the "Try Ubuntu" feature of the Ubuntu installation CD as well as to install Ubuntu directly from an ISO on the hard drive. In addition to Ubuntu ISOs, many other Linux distributions as well as popular [FONT=inherit]rescue[/FONT] CDs can be booted directly from an ISO file. [COLOR=#222222][FONT=Verdana]

Regards.[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by sudodus on 2013-11-20
I have installed Puppy manually booting from the iso file and saving data to a file specified in [FONT=courier new]**/etc/grub.d/40_custom**[/FONT] (in a system with Ubuntu 12.04 LTS and grub2), so I should be able to help the original poster.

---

### Post by Frogs Hair on 2013-11-20
According to the documentation at the link you will need 2Gb drive for a standard installation .

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There  is a "Mini ISO", but it is version specific for use with USB and I have never installed this way. I think using the minimal installation  would entail installing all the packages from the command line to get fully functional Ubuntu. Wait for further replies because I simply haven't used this installation method before. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by alistair_gower-j on 2013-11-20
Thanks, I'll try all the above. It's a Toshiba Satellite L750-1RJ, 320gb Hard Drive, 4gb Ram, intel i3-2330m processor with a Nvidia GeForce GT525M graphics card[COLOR=#6d6f72][FONT=arial, helvetica, verdana, sans-serif].[/FONT][FONT=arial black] [/FONT][/COLOR]I have tried to restore windows using the toshiba system restore but to no avail which is why I am attempting to run linux instead. It'll be used as a very general purpose laptop, used for studies and general entertainment purposes. If not Ubuntu then what would you suggest?

---

### Post by sudodus on 2013-11-20
> **Frogs Hair said:**
> According to the documentation at the link you will need 2Gb drive for a standard installation .

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There  is a "Mini ISO", but it is version specific for use with USB and I have never installed this way. I think using the minimal installation  would entail installing all the packages from the command line to get fully functional Ubuntu. Wait for further replies because I simply haven't used this installation method before. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Yes, but that is not true. The iso file is smaller than 1 GB, and it works in a 1GB pendrive, definitely with the mkusb method (using dd behind the curtain), and I think also with Unetbootin. But today, the smallest pendrives you can buy contain 2 GB, maybe that is the reason for that statement (I have edited that page, but not changed old parts).

---

### Post by sudodus on 2013-11-20
> **alistair_gower-j said:**
> Thanks, I'll try all the above. It's a Toshiba Satellite L750-1RJ, 320gb Hard Drive, 4gb Ram, intel i3-2330m processor with a Nvidia GeForce GT525M graphics card[COLOR=#6d6f72][FONT=arial].[/FONT][/COLOR]I have tried to restore windows using the toshiba system restore but to no avail which is why I am attempting to run linux instead. It'll be used as a very general purpose laptop, used for studies and general entertainment purposes. If not Ubuntu then what would you suggest?

The computer specs indicate that Ubuntu would work. If you want good performance withe high definition video, it might work better with a desktop environment with a lighter foot-print than standard Ubuntu with Unity, for example Xubuntu.

Try either the long time support version 12.04 LTS, or the newest version 13.10. Try live before deciding what to install.

---

