---
title: "Dual Boot Windows 10 &amp; Ubuntu Mate (or any flavor) on Dell Inspiron 5559"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by gdavidrath on 2016-05-15
I bought a new DELL with with Windows 10 at Costco, and I want to dual boot with Ubuntu.

Unfortunately, though I've tried several different settings in the UEFI BIOS, and tried putting the boot loader in different places-I've even tried EasyBCD. But I still can't get the process down right. After installing Ubuntu, I either get "no operating system found" or I'm back to Windows 10 without a Ubuntu option.

I CAN boot Ubuntu from a flash drive using "shift & cntrl" when shutting down Windows 10, then choosing the "boot from a flash drive" option. For me, this is a last resort. I'd really like to be able to dual boot.

I'd appreciate some guidance.

Thanks!
David

---

### Post by Bucky Ball on 2016-05-15
Welcome. Boot to Windows and switch off hibernation/fast start. Switch off secureboot in the BIOS. EasyBCD is not required and may only confuse the issue.  

There is a link to Boot Repair in my signature at the bottom of this post (last link). Try that in a live session and run the bootinfo script, not the 'Recommended Repair'. When finished, you will be presented with a link to the output. Post that here, please.

---

### Post by oldfred on 2016-05-15
In addition to Bucky's suggestions.

Make sure you boot flash drive in UEFI boot mode. It may require settings in UEFI to allow USB boot and UEFI or CSM/BIOS boot mode on USB. Every UEFI is somewhat different on what settings are required.

With UEFI (and BIOS) you install grub to a drive like sda, not to a partition like sda1 or sda5. But with UEFI grub only installs to the ESP - efi system partition on sda, which with one drive is the correct location, but can be an issue with multiple drive installs.

---

### Post by gdavidrath on 2016-05-16
Hi Bucky and Oldfred,
Here is the output from the bootinfo script: [http://paste.ubuntu.com/16468549/](http://paste.ubuntu.com/16468549/).

Thanks in advance for your help!
David

---

### Post by oldfred on 2016-05-16
It looks like you installed Ubuntu in BIOS boot mode, but have Windows in UEFI boot mode.
The two modes are not compatible, once you start booting in one mode you cannot switch. Or from grub you cannot dual boot. But should be able to boot from UEFI if you have grub in correct place.

For BIOS boot grub must be in MBR, not a partition boot sector or PBR where you installed it.

Probably better to convert Ubuntu to UEFI boot. Boot-Repair can do that in advanced mode with a total uninstall/reinstall of grub. It uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI). 
You must have Internet working and best to use wired connection.

---

### Post by gdavidrath on 2016-05-19
I couldn't figure out how to convert my existing Ubuntu installation to UEFI boot, but it didn't matter because it was fresh install. So I reinstalled Mate. This time I made sure UEFI was ON in BIOS and I installed GRUB to the Windows Boot Loader. Now I am able to dual boot Ubuntu Mate & Windows 10.

Thanks so much for your help!
David

---

### Post by oldfred on 2016-05-19
Glad  you got it working.

You can change to [Solved].

---

