---
title: "Issues with new installation of Ubuntu as a dual-boot option"
date: 2023-07-04
forum: Installation &amp; Upgrades
---

### Post by arkane-fire on 2023-07-04
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]Apologies as I'm new to Ubuntu, but I had wanted to install this to enable me to undertake some data processing within a Linux based system.[/COLOR]

[COLOR=#000000]I flashed an ISO of Ubuntu to a USB drive and used this to install on an older HP laptop (HP Elitebook Corei5 vPRO), so that I could then boot alongside windows. The installation all went according to the instructions and when I then rebooted the laptop I got the options attached (image; Ubuntu boot menu). If I select Ubuntu this boots fine. However, if I select windows I get the attached error message (image; windows error).[/COLOR]

[COLOR=#000000]Any ideas what I've done wrong........ If all else fails I will just have to fresh install windows and start again....[/COLOR]

[COLOR=#000000]Thank you for your help,[/COLOR]
[COLOR=#000000]Robin.[/COLOR]

---

### Post by grahammechanical on 2023-07-04
Just to be clear. You install Ubuntu. The first reboot you get the Grub boot menu and load Ubuntu. The second reboot you choose Windows at the Grub menu and then get this error. I am correct?

It should be possible to load Windows from the UEFI settings utility. Windows must have fast startup disabled as it is a kind of hibernation that prevents Linux from reading the Windows partitions. 

Windows updates always reset fast start up

Regards

---

### Post by tea for one on 2023-07-04
Are you familiar with Legacy and UEFI installations?
More info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It would be useful if you could provide a boot-repair report.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

---

### Post by ubfan1 on 2023-07-04
"drivemap" indicates a legacy grub.cfg, so problem is likely UEFI vs legacy.  How the Ubuntu is made depends upon how the install media boots, and that depends upon machine settings (legacy=csm, vs uefi).  Check that Windows is a UEFI install (gpt partition table, not msdos), and confirm that the machine settings will do UEFI in preference to legacy.

---

### Post by arkane-fire on 2023-07-04
> **grahammechanical said:**
> Just to be clear. You install Ubuntu. The first reboot you get the Grub boot menu and load Ubuntu. The second reboot you choose Windows at the Grub menu and then get this error. I am correct?

It should be possible to load Windows from the UEFI settings utility. Windows must have fast startup disabled as it is a kind of hibernation that prevents Linux from reading the Windows partitions. 

Windows updates always reset fast start up

Regards

Yes that's right, I get the GRUB menu, but windows won't boot if selected from here (but Ubuntu will). I can enter BIOS/UEFI via F10, before this menu. But I'm unsure how to load windows from here (I've attached an image of the boot order). Any advice would be much appreciated.

---

### Post by arkane-fire on 2023-07-04
> **ubfan1 said:**
> "drivemap" indicates a legacy grub.cfg, so problem is likely UEFI vs legacy.  How the Ubuntu is made depends upon how the install media boots, and that depends upon machine settings (legacy=csm, vs uefi).  Check that Windows is a UEFI install (gpt partition table, not msdos), and confirm that the machine settings will do UEFI in preference to legacy.

Thank you for responding, what would be the best way to go about this?

---

### Post by ubfan1 on 2023-07-04
From Ubuntu, run sudo fdisk -l (that's a small L) and see what the disklabel type is, gpt or msdos.  If gpt, then Windows is in UEFI mode.  If you Ubuntu install was with the UEFI setting in your image (uefi), then Ubuntu is also in UEFI mode.  Both should be in the same mode, so the easiest fix if they are different is to reinstall Ubuntu in the same mode Windows is in (Change the UEFI setting if necessary).

---

### Post by yancek on 2023-07-05
If you have not resolved this issue, I would suggest that you download and run boot repair as suggested in post #3 (link is available there).  The image you posted in post 5 shows an entry for OS Boot Manager which is likely windows which was the default OS installed.  Have you tried using the arrow keys on the keyboard to highlight that entry and hit the enter key to select it?  There is no entry for Ubuntu shown so you likely have Ubuntu in Legacy/CSM mode while windows is UEFI.  In this situation, the Ubuntu Grub bootloader will not boot windows.

---

### Post by SeijiSensei on 2023-07-05
Creating the boot device using Rufus in Windows makes choosing the correct disk format easy.

[https://rufus.ie/en/](https://rufus.ie/en/)

---

