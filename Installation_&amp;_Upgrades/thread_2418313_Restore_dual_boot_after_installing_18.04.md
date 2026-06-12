---
title: "Restore dual boot after installing 18.04"
date: 2019-05-05
forum: Installation &amp; Upgrades
---

### Post by jackhab on 2019-05-05
I installed 18.04 on an old laptop with Windows 7 booting from MBR.

Ubuntu is installed on a separate partitions (see attached file) and boots in UEFI mode but I can no longer boot Windows (got invalid partition message).

How can I fix the boot loader?

Thanks.

[ATTACH=CONFIG]283191[/ATTACH]

---

### Post by ajgreeny on 2019-05-05
For a dual boot of Windows and ubuntu to allow you to choose which OS to boot to from the grub menu both OSs must use the same system,  MBR or UEFI.

If you have not used Ubuntu much so far and have not spent a lot of time configuring the system it may be easiest to start again with the Ubuntu install, but this time use an MBR installation.

To give us more detailed info it will be best to see exactly where you are at present, so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run any default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

See also the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which you may find helpful.

---

### Post by jackhab on 2019-05-05
[http://paste.ubuntu.com/p/gms57Gzy9T/](http://paste.ubuntu.com/p/gms57Gzy9T/)

---

### Post by oldfred on 2019-05-05
You have new UEFI hardware, but Windows installed in the old BIOS/MBR configuration on MBR partitioned drive.
Windows only boots from MBR with BIOS and only with UEFI from gpt, so not easy to convert Windows to UEFI boot without full backup, repartition and reinstall. Since Windows reinstall a lot more difficult than Ubuntu reinstall/repair better to make Ubuntu BIOS boot. Ubuntu lets you install in UEFI mode to MBR partitioned drives even though gpt highly recommended by UEFI.

You cannot have two boot flags on one drive. But UEFI requires boot/esp flags on the ESP - efi system partition (your sda7) and Windows requires the boot flag on its Boot partition (your sda2). So remove boot flag from sda7 and put on sda2. Make sure Windows boots ok.
Grub only boots working Windows, so be sure to have a Windows 7 repair disk to restore Windows boot loader or make Windows repairs.

Then use Boot-Repair to run its fix which will uninstall grub-efi-amd64 (UEFI) and install grub-pc(BIOS). You do not have to do a full reinstall, but can if desired. 
Grub does not use boot flag to find Windows bootable partition, so it will find it & allow boot. But if Windows needs repair, it only uses boot flag to know which partition is Windows, so will not repair it, if you have boot flag on an ESP.

Or very difficult to dual boot Windows in BIOS and Ubuntu in UEFI boot mode. May be able to move boot flag back & forth before rebooting in other system, if systems otherwise correctly configured.

---

