---
title: "Updating Bios/UEFI"
date: 2022-08-11
forum: Installation &amp; Upgrades
---

### Post by dorpapst on 2022-08-11
Hey,
For some reason I need to update my bios on my computer. I have experience in all sorts of upgrading on my PC, but never upgraded my bios in any way. So I am a bit nervous about that.
I have a *B550M AORUS ELITE *and my current bios version is F13. The newest one is F15.
When I download the zip file with the new firmware, I get four files:
- autoexec.bat
- B550MAE.15c
- Efiflash.exe

I only have Ubuntu 20.04 on my computer, no windows or other stuff. It makes me a bit nervous having an .exe there.

What is the most intuitive way of getting these three files into my bios? I know I need to flash that onto an usb device, but is that possible with the exe file and how would I do that?

Thanks for any help.

---

### Post by oldfred on 2022-08-11
Most motherboards have several ways to update UEFI.
You can create a FAT32 flash drive with the update file, put the update file in any FAT32 partition in system or create a DOS type bootable flash drive.
UEFI can directly read FAT32 partitions.
So I typically make my ESP larger, so it has room for backups & UEFI update files. I do have to change permissions in fstab from 0077 to defaults to allow me to do that from within my system.

Download your motherboard manual and review details for your motherboard. Manual is on same site as you downloaded update.

---

### Post by bingodingo on 2022-08-11
Hi,
make sure you really need to update the bios, if it goes wrong you can brick your motherboard.
F15c and F15a for your board are beta (that's what the letter says with gigabyte), F14 is the latest stable - use F14 unless you really need something on F15x (e.g. Agesa v2 1.2.0.7).

There are directions you can follow at this url:
[https://support.punchtechnology.co.uk/hc/en-us/articles/360016785438-How-to-update-the-BIOS-on-your-Gigabyte-B550M-Aorus-Elite-motherboard-F15b-](https://support.punchtechnology.co.uk/hc/en-us/articles/360016785438-How-to-update-the-BIOS-on-your-Gigabyte-B550M-Aorus-Elite-motherboard-F15b-)

You can't use the exe files within linux (and I wouldn't recommend them anyway).
Basically: download the zip, decompress - either to a usb (FAT32 formatted) or your computer. If your computer: copy the B55MAOEL.Fxx (e.g. B55MAOEL.F14 or B55MAOEL.F15c) to the usb - this is the file you need.
(Safest option is to have only the bios update file on the usb - this reduces the chance of selecting the wrong file; some update software will check compatibility, but I wouldn't rely on that. 
You could access the file directly off a FAT32 system partition but I think if you use a usb you reduce the chances of things going wrong.)
Boot into bios with the usb connected to your computer (following above directions), use Q-Flash to update with the above mentioned file (following above directions).
Bonus points: 
1. if you get blackouts (e.g. possums on the wire at night around here) try to avoid those times (you can brick your motherboard).
2. match the usb to the port your using on the computer for maximum stability (e.g. usb2 with usb2 port).
3. have a disaster plan before hand (e.g. some motherboard's have special options for recovering motherboard with a mangled bios update, your mileage may vary).

---

