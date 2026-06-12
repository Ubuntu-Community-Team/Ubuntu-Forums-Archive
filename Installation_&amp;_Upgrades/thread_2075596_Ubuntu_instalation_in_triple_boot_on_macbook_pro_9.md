---
title: "Ubuntu instalation in triple boot on macbook pro 9.2"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by avedzovg on 2012-10-24
Hi there,

I am at my wits end. Would be grateful for any help. I bought macbook pro 9.2 and tried to install triple boot (OSX/Win7/Ubuntu). 

As in instruction I used disk utility and divided the hard drive into 3 partitions. I installed rEFIt and tried to install Windows 7. Everything went well. I had working Win7 on the laptop and one free partition to go. 

I created live dvd and booting usb with Ubuntu 12.04amd64. Live dvd does not work at all. It gives black screen and blinking  white "_" in the left top corner. I could not type or do a thing. With booting usb I had no luck as well and got "No default or UI configuration directive found!" I followed some internet advise and renamed folder isolinux into syslinux. (the same for files isolinux.bin and isolinux.cfg). With this I was able to see the booting menu, but could not install the system because of the kernel panic: "Kernel panic - not syncing: timer does not work through interrupt-remapped 10 apic". I tried to install the same image with the option acpi=off. It helped and installation started, but keyboard was not active, so I could not type name, login and so on. I tried to install again with the option noapic and it went great. But after the first reboot I got "operating system is not found". 

Tried to install it again and again, tried to follow some advise and fix refit tables and reinstall grub under the "try ubuntu", but was not able to (it said that everything is synced).  During Ubuntu installation I created a lot of small partitions, which I formatted and merged into one in OSX. Windows worked at that time. 

I downloaded Ubuntu12.04amd64+mac and tried to install again. Live dvd was useless again. Bootable usb could install the system only with noapic, but I still got "operating system is not found". Somewhere in the middle of everything windows stopped working. I decided to erase everything and try again. I merged and erased everything and divided into 3 partitions again, but something have happened with firmware, as I can not even install windows anymore. EFFI partition disappeared. Now, for some reason, I have 2 disks (it was only one in the beginning) and EFFI is installed on the second one. At every boot I still have a choice of linux boot from Refit (it seems it was created on the second disk).  I tried to update firmware, but I have got an error "This software is not supported on your system." (Firmware is for mid 2012). OSX is still working.  

Could someone please help me? I am stuck with OSX:( I prefer Ubuntu, but still want to have OSX and Win7 just in case.

---

### Post by irie on 2012-11-07
Try this, when booting off the bootable USB, hold the Option key down until the boot partitions show up.  Do you see OSX, Windows, Windows, EFI?  If so, choose the EFI option.  You should then see the Ubuntu boot menu.

---

### Post by offgridguy on 2012-11-07
There might be another way to go, if you look at this thread,  there is some discussion about dual boot on a mac.

[http://ubuntuforums.org/showthread.php?t=2081105&page=2](http://ubuntuforums.org/showthread.php?t=2081105&page=2)

Hope it helps.

---

