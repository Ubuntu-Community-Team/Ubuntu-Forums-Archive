---
title: "xubuntu dual boot"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by joshbrice on 2012-12-26
Ok so installed xubuntu next to windows 7 but when it gets to the grub boot loader to choose between windows and linux it will only boot to linux.  When I choose windows 7 it gives me a blank screen with a flashing dos cursor.

All the windows files are intact I checked.

Any help would be greatly appreciated!

---

### Post by oldfred on 2012-12-26
Do you have Windows repairCD or full install set to run Windows repairs? How did you resize the Windows partition. With Windows MMC, gparted or Ubuntu installer. Windows always has to run chkdsk after a resize and usually best to use Windows to resize and reboot before install.

This will not normally fix Windows issues but will let us suggest what to do. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

