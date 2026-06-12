---
title: "No operating system found after installation lubuntu"
date: 2022-10-30
forum: Installation &amp; Upgrades
---

### Post by lajolla on 2022-10-30
Hi! So I'm trying to install lubuntu as it's more light weight. But I can't for the life of me get it to work. It boots great from the USB, I get to test out the OS etc. I go through the install, erase disk and reformat. Installation goes well, restart computer and it tells me to remove USB and hit enter and I hit enter and and get 1962 no operating system found. The installation gave no errors or indications it didn't go through, it even told me it was finished. I'm very stuck, I've looked everywhere for a solution but can't seem to find one.

I install it with CSM disabled UEFI mode as recommended. 

Computer is: Lenovo H505S AMD Dual Core E2-1800 1.7GHz, 8 GB ram, 120 GB SSD only one harddrive.

---

### Post by tea for one on 2022-10-30
Can you access your UEFI Set Up and check the following:-

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot 
Disable Legacy mode 
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by lajolla on 2022-10-30
Disable secure boot: disabled
CSM: Disabled
Boot mode: Auto (can't be changed)
Boot priority: UEFI first (can't be changed)
Quick boot: disabled 
SATA MODE: IDE

Disable legacy mode, can't be found same with rest. 

After those settings i get sent to setup immediately nothing installed. Put the usb in to try a reinstall and now I'm stuck on Lenovo screen

---

### Post by grahammechanical on 2022-10-30
I found this:

> **Change Boot Order in BIOS**
   If the cause of the error 1962 lies within the BIOS, changing the  boot order, or priority, should fix the problem. Follow the steps below  to change the boot priority.

    
[LIST=1]
[*]When &#8220;Error 1962: No Operating System Found&#8221; appears on your screen, hold the &#8220;Ctrl+Alt+Delete&#8221; keys down to reboot your device
[*]While your device is booting, press F12 multiple times to open BIOS setup, then press enter
[*]Click the startup tab, select CSM, hit enter, and then select &#8220;enabled&#8221;
[*]Select the boot priority option and hit enter, change current option of legacy first to UEFI first
[*]Press the F10 key and choose yes. Your device should then reboot
[/LIST]

From here

[https://www.gillware.com/lenovo-error-1962-no-operating-system/](https://www.gillware.com/lenovo-error-1962-no-operating-system/)

I am guessing that Lubuntu was one stalled in one mode (legacy/bios/csm or UEFI) and the motherboard is set to boot an OS in the other mode (UEFI or legacy/bios/csm).

Regards

---

### Post by oldfred on 2022-10-30
SATA mode is normally AHCI. IDE is a really old standard.
CSM, legacy, & BIOS are all the same thing. Generally its UEFI or CSM, or perhaps both.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

How you boot install media, UEFI or BIOS in UEFI boot menu, is then how it installs.
Then in UEFI/BIOS settings you have to have it set to boot in that same mode.
Systems since 2012 are UEFI as Microsoft required all vendors to install in UEFI boot mode to gpt partitioned drives to install Windows 8.
Many new system, starting in 2021 or so are now UEFI only. No CSM mode at all.

---

### Post by lajolla on 2022-10-30
> **grahammechanical said:**
> I found this:


[/LIST]

From here

[https://www.gillware.com/lenovo-error-1962-no-operating-system/](https://www.gillware.com/lenovo-error-1962-no-operating-system/)

I am guessing that Lubuntu was one stalled in one mode (legacy/bios/csm or UEFI) and the motherboard is set to boot an OS in the other mode (UEFI or legacy/bios/csm).

Regards

> **oldfred said:**
> SATA mode is normally AHCI. IDE is a really old standard.
CSM, legacy, & BIOS are all the same thing. Generally its UEFI or CSM, or perhaps both.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

How you boot install media, UEFI or BIOS in UEFI boot menu, is then how it installs.
Then in UEFI/BIOS settings you have to have it set to boot in that same mode.
Systems since 2012 are UEFI as Microsoft required all vendors to install in UEFI boot mode to gpt partitioned drives to install Windows 8.
Many new system, starting in 2021 or so are now UEFI only. No CSM mode at all.

Thank you both! Changed SATA to ACHI and eufi on legacy and it did the trick. Everything works perfectly now :)! Finally I can let go of my weekend headache and hair dragging trying to figure this out.

---

