---
title: "can't boot to windows 8 after ubuntu 12.04 LTS installation"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by pratir on 2013-07-19
I have a HP Pavilion Touchsmart laptop which came initially with Windows 8 OS. I disabled the secure boot then, installed ubuntu 12.04 LTS on a separate partition (dual boot). Now I cannot boot windows 8. Selecting the windows 8 option the following error is displayed
```
error: unknown command 'drivemap'
error: invalid EFI file path.

```
I ran the boot-repair once but still the same problem persists.
Boot-repair: [[COLOR=#1155cc][FONT=Arial]_[http://paste.ubuntu.com/5890413](http://paste.ubuntu.com/5890413)_[/FONT][/COLOR]]("http://paste.ubuntu.com/5890413")

---

### Post by Boab1993 on 2013-07-19
It sounds like you've deleted your windows boot partition, sadly. 
The drivemap is so it can load your OS onto memory, if it doesnt exist then you very well may need to re-install windows 8. 
Other people on here more experienced with windows 8 might be able to help.

Sorry i cant!

---

### Post by oldfred on 2013-07-19
If it is Windows 8 that is UEFI. But it sounds like you installed Ubuntu in BIOS/CSM/Legacy mode? UEFI and BIOS write hardware system data differently for system to use so booting from BIOS will not let you boot Windows from grub. Also grub has a bug and writes BIOS boot entries even if Ubuntu is in UEFI mode. You can use Boot-Repair to convert to UEFI or to add correct UEFI Windows boot entries.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

