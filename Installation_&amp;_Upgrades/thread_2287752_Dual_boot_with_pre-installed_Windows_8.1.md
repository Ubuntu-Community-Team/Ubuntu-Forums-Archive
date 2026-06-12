---
title: "Dual boot with pre-installed Windows 8.1"
date: 2015-07-22
forum: Installation &amp; Upgrades
---

### Post by ashu2 on 2015-07-22
I had got a new Windows 8.1 laptop. I created linux partitions via diskmgmt and then downloaded the ISO image of 64 bit 1.x version Ubuntu Desktop. As the bios was not getting booted...i disabled secure boot as well as enabled legacy bios mode. Also within Windows o/w i disabled quick start. But after that i am not able to boot from the live usb even after changing the boot order, why?
when i am using legacy bios mode and then going into "try ubuntu" and then sudo boot-repair. It's giving me warning to first enable secure boot and disable legacy BIOS. So it's chicken and egg issue.

---

### Post by oldfred on 2015-07-22
What brand/model system?
If Windows is UEFI then much better to install Ubuntu in UEFI mode. And if you want to use grub menu to dual boot, you need UEFI secure boot off, but UEFI on or CSM/BIOS/Legacy off.

Some systems require you to specifically allow UEFI boot of external devices. I think that is a security setting. A few (Acer for one) require you to set a password to open up extra settings that you need to change including "trust" for ubuntu boot entry.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

