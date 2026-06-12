---
title: "Help with installing Ubuntu on UEFI based system"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by jekintrivedi on 2014-07-16
Help with installing Ubuntu 14.04 on UEFI (Win 8.1) system 

Hey I tried following the steps mentioned on : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

But Still i am not able to see the Boot Manager and the laptop boots directly to Win 8. 

This is the file generated after running boot repair. 

[http://paste.ubuntu.com/7805115/](http://paste.ubuntu.com/7805115/)


PS : I also tried to convert my existing installed Ubuntu into EFI mode. Still didnt got the boot manager and also fogot to save the link for the boot repair this second time.

PPS : Followed this Post ([http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)). Problem solved. The steps mentioned in Ubuntu  help Community ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) is kind of incomplete.

---

### Post by oldfred on 2014-07-16
It says grub installed correctly and it is in UEFI. Can you boot Ubuntu entry from UEFI menu or one time boot key often f12 but varies by vendor.
What vendor & model computer?

       BootOrder: 0000,000A,0001,0007,0008
Boot0001* Windows Boot Manager
Boot0007* UEFI: IP4 Qualcomm Atheros PCIe Network Controller
Boot0008* UEFI: IP6 Qualcomm Atheros PCIe Network Controller
Boot000A* UEFI: General USB Flash Disk 1.0
Boot0000* [COLOR=#ff0000]ubuntu[/COLOR],BootCurrent: 000A

Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

Sony & HP maybe others modify UEFI to only boot Windows and work around required.

---

### Post by jekintrivedi on 2014-07-16
Hey oldfred thanks for the reply. I just did  [COLOR=#666666]*bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi *[/COLOR]from windows and it worked.

---

