---
title: "Ive installed ubuntu on my windows dual boot system."
date: 2023-12-05
forum: Installation &amp; Upgrades
---

### Post by billy.j.subs on 2023-12-05
Windows loads fine but ubuntu doesnt.

Here is the pastebin record, how do i get the system to boot from =my ubuntu install? 

I have installed boot-repair but just waiting for the next steps

[https://paste.ubuntu.com/p/bS9tdN6vw5/](https://paste.ubuntu.com/p/bS9tdN6vw5/)


It cant find the boot files when i select to boot from the sata drive

Windows is on the nvme drive and ubuntu is on the sata drive

/dev/sdc is my usb boot stick/drive that im booting from to fix the issue


Many thanks

Billy

---

### Post by tea for one on 2023-12-05
Lines 67 - 69 - sdb1 File system:       BIOS Boot partition
This indicates that you installed Ubuntu in Legacy mode while Windows is in UEFI mode

Line 122 - The firmware is EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode)
Also, you have booted the live session in Legacy mode.

Power off the PC
If possible disable Legacy boot in your UEFI settings
Try and boot Ubuntu in UEFI mode

---

### Post by oldfred on 2023-12-05
UEFI install typically defaults to ESP - efi system partition on first drive.
Your fstab shows the UUID of the ESP on the NVMe drive.
That works fine, but some of us like to have boot files on same drive as install. 

If you cannot boot in UEFI mode, reboot live installer in UEFI mode and then Boot-Repair should offer to reinstall grub in UEFI boot mode, if not use advanced mode.
If you use advanced mode, you then can choose which drive to install grub into, your choice. Default probably will be the ESP on NVMe drive.

How you boot install media, Windows or Ubuntu is then how it installs and how it repairs.
Since you have UEFI hardware, you always want to boot in UEFI boot mode.

UEFI settings should have setting for UEFI or Legacy/CSM/BIOS mode and then if UEFI on either Secure boot on or off. If install of Ubuntu is with Secure boot off, you have to keep UEFI setting to off. 
USB boot usually gives you two choices one clearly UEFI and one just name or label of flash drive which then is the BIOS boot option. Always choose the UEFI: XXXX option where XXXX is name or label of live installer flash drive.

---

### Post by billy.j.subs on 2023-12-05
Thanks for the responses guys. one thing that always confuses me is EFI.....the issue with my install was that it was install via a legacy boot on the USB boot drive...not the USB boot with EFI!
 As efi was not enabled at boot ,....%)

---

### Post by oldfred on 2023-12-05
The standard install ISO is configured for both UEFI and BIOS/CSM/legacy boot.
Most installers create live installer flash drive in both modes, so user can choose when booting system.
Some install tools create either UEFI only or BIOS only installer. 
Since your system is UEFI, always choose UEFI.

New systems starting in about 2020, depending on brand, are UEFI only. Helps avoid issues as BIOS mode does not even work.

---

### Post by ubfan1 on 2023-12-05
Some pcs' settings have you set an order preference -- UEFI before legacy or vice versa.  If your machine was to prefer legacy, but your Windows was only UEFI, it would boot UEFI. The Ubuntu installer (may) have both, so it booted legacy.   Possible explanation.

---

### Post by fullscale4me on 2023-12-08
In the paste on line 264    **GRUB_TIMEOUT=0**

The user gets no chance to choose anything other than the default. Using a Grub boot repair to set it to 10 or 15 (seconds) might be helpful.

At power on is there a on-screen indication to change Boot? F12 is used a lot.

---

### Post by yancek on 2023-12-09
Given that windows is booting and there is no option to boot windows, it would seem to me that the nvme drive is set to first boot priority in the BIOS firmware and changing that to set the Ubuntu drive (sdb) to first boot priority would resolve the problem.  My experience is that a Legacy/MBR install of Linux using Grub will boot an EFI install of windows as long as the systems are on separate drives.  As far as the timeout, I don't think the OP sees the Grub menu from what was posted but that would be a problem if the change in device to boot is made.

Installing both EFI would be the simplest and best method.

---

