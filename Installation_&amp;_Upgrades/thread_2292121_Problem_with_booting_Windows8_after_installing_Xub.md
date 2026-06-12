---
title: "Problem with booting Windows8 after installing Xubuntu 14.04"
date: 2015-08-25
forum: Installation &amp; Upgrades
---

### Post by Nicolas_Castro on 2015-08-25
Hi guys i have just installed Xubuntu, and when i was installing it, it made me create a different partition for the boot, cause it said it could cause an error if i didn't create it, so i did it. But now in the startup menu if i choose Windows 8Os then appear an error page, saying ther might be an error in the boot caused by some program. Of course if i choose Xubuntu it's working fine. Also if I go to the Bios setup and choose UEFI first in the Boot priority then starts in Windows 8 with no problem. But then i don't have the option for Xubuntu. Can i fix that issue, or everytime i want to start  in a different OS i need to go to the BIOS setup?
Thank you, very much.

---

### Post by oldfred on 2015-08-25
It sounds like you created a bios_grub partition which with gpt partitioning is required for grub to install in the protective MBR for BIOS boot.
But Windows is installed for UEFI boot. 
And UEFI & BIOS are not compatible, so you have to go into UEFI to change boot modes.
You may be able to use one time boot key like f10 or f12 check you manual.

You can convert Ubuntu to UEFI boot with Boot-Repair's advanced mode, it uninstalls grub-pc (BIOS) and installs grub-efi-amd64(UEFI) which also changes a few other settings so then it is UEFI bootable. Be sure to boot in UEFI mode.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    How you boot installer is then how it installs, so always boot in UEFI mode. From UEFI you should have two choices to boot Ubuntu live installer, one UEFI and one BIOS.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Nicolas_Castro on 2015-08-31
Thank you very much Oldfred, i have already installed boot-repair, should i do the recommended repair or try the advanced? if i click the advanced option, how can i change the grub to UEFI?

---

### Post by Nicolas_Castro on 2015-08-31
If i boot in UEFI mode it takes me directly to Windows...

---

### Post by oldfred on 2015-08-31
In Boot-Repair's advanced mode should be a total uninstall/reinstall of grub. Probably best to boot Boot-Repair in UEFI mode, but I think it can convert even if in BIOS mode. It actually uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI).

---

### Post by Nicolas_Castro on 2015-09-01
Thank you very much. But I still have problems. I boot with the Boot repair disk but then ask me for internet connection, and again doesn't recognize my lenovo wireless... So it doesn't allow me to repair the boot without an internet connection... 
Here is how i fixed the problem with Xubunutu [http://ubuntuforums.org/showthread.php?t=2291922](http://ubuntuforums.org/showthread.php?t=2291922). Guess that with the Lubuntu of the Boot repair should be the same but now i've got no wire to connect it...

---

