---
title: "Dual boot, 12.10 and Windows on Toshiba Satellite"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by drken on 2013-02-15
I have a Toshiba Satellite laptop with Windows 7 installed.  I desperately want to learn Ubuntu and install it on my laptop alongside Windows 7 (preferred) or in place of Windows 7 (acceptable if I can not have both coexist on the hard drive).  I have tried several downloads of 12.10 and can not get it to install on the hard drive.  I have also been searching the forums here for the past 2 weeks, and just haven't had much luck in finding anything that would assist me in installing 12.10 on the Toshiba Satellite.

If anyone here can help, I sure would aprpeciate it!  Please keep in mind that I do not know Unix, Linux, Ubuntu, etc. - it's all new to me.

Thanks in advance.

Ken

---

### Post by Mossey on 2013-02-15
You need to know if you have UEFI bios first. If not you can make an installation USB or CD using Unetbootin. Just download and run the .exe and choose your desired installation.
If you have a UEFI bios, then you can do the same steps above, but then you need to reboot and change bios setting and disable the secure boot(under security section) then restart. It should boot to the USB/CD then you should have the option to try Ubuntu or install. I always choose to try Ubuntu just until I get the hang of it. I can't get Skype on the 64 bit version working.
If you have the UEFI bios and you choose to install Ubuntu alongside Windows you probably will have another host of issues, with booting and having to change Grub settings by running the boot repair.

---

### Post by oldfred on 2013-02-16
If Windows 7 was default, you will not have secure boot issue with UEFI as that is only Windows 8 pre-installed systems. While some newer Windows 7 systems have UEFI, most were installed in BIOS mode.

But if in BIOS mode you have the 4 primary partition limit. 

From liveCD terminal post this.

sudo parted -l

---

