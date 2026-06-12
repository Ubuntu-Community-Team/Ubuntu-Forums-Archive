---
title: "Fresh Install....operating system not found"
date: 2023-05-21
forum: Installation &amp; Upgrades
---

### Post by MadMonkey1966 on 2023-05-21
Hi Everyone, been using Mint (and various other flavours on laptop) for years now after starting with Ubuntu. Last year i got my sister a Lenovo Thinkcentre, but now she has a work provided machine, she has given me it back.

Anyway, i decided to wipe it & put the latest Ubuntu on it. All went fine with the installation until it re-booted.

Now it comes up with:

[B]Intel(R) Boot Agent GE v1.3.81
Copyright.......

Initializing and establishing link....
[/B]
then
 [B]
PXE-E61: Media test failure, check cable
PXE-m07: Exiting Intel Boot Agent

[/B]then

[B]Error 1962: No operating system found, press any key.....
[/B]
I have tried changing all sorts in the BIOS and tested the HD in another PC (Ubuntu is on it & runs fine). 
I have also searched Google & asked ChatGPT, the latter telling me it was trying to boot from a network (so i have removed that from the boot sequence), now i just get the [B]Error 1962: No operating system found, press any key..... 
[/B]
Does anyone have any ideas, what could be causing it as i know the HD is ok, and Ubuntu is on there & working.
Any help would be much appreciated.

Ian :cool:

---

### Post by tea for one on 2023-05-21
> **MadMonkey1966 said:**
> I have tried changing all sorts in the BIOS and tested the HD in another PC (Ubuntu is on it & runs fine). 
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST 
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Disable Device Guard (some Lenovo devices)
Disable OS Optimised Defaults (some Lenovo devices)

---

### Post by MadMonkey1966 on 2023-05-21
Thanks for the reply. I have checked all those, and the ones I have seemed all OK&#8230;

I just tried the One-time boot menu & it gives me the option to boot from the HDD, but I just get the [B]Error 1962: No operating system found, press any key.....

[/B]I guess it could be then lead from Motherboard to HDD, but would be a huge coincidence it if happened to break just as I installed a new system......

I am confused :confused:

---

### Post by tea for one on 2023-05-21
Did you install in UEFI mode?

---

### Post by MadMonkey1966 on 2023-05-21
thanks for your time.....I think it was just set to AUTO....... I have done more digging & run Boot-repair from live-USB..... Here is the URL of the report...

[https://paste.ubuntu.com/p/PpQRZST5QZ/](https://paste.ubuntu.com/p/PpQRZST5QZ/)

It seems, you may have nailed it as the report says a similar thing...
> Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda3,
using the following options:  sda2/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.2 LTS entry (sda2/efi/****/grub****.efi (**** will be updated in the final message) file) !

So is it best to run Boot_repair again & let it rectify the issue, or is there a better way ? :)

---

### Post by tea for one on 2023-05-21
[COLOR="#0000FF"]Line 22 to 24[/COLOR] - sda1:    File system:       BIOS Boot partition
This line indicates that you booted and installed in Legacy mode.
When you install in UEFI mode, the installer does not create a BIOS Boot partition.

Try the default repair because I assume you have no data to lose?

---

### Post by MadMonkey1966 on 2023-05-21
Correct, Nothing on there to lose at all. 
I Tried it, it did run but finished with an Error: NVram is locked (Ubuntu not found in efibootmgr). Please report to [email]boot.repair@gamil.com[/email]

[https://paste.ubuntu.com/p/Jrb5ByGhP6/](https://paste.ubuntu.com/p/Jrb5ByGhP6/)

I tried a reboot, but still no change.

If i create a fresh Live USB, and set Partition to GPT & target system to UEFI, and then reinstall, would that work ???

---

### Post by tea for one on 2023-05-21
> **MadMonkey1966 said:**
> I Tried it, it did run but finished with an Error: NVram is locked (Ubuntu not found in efibootmgr)
This locked NVram business is becoming more frequent and, regrettably, I've never seen a reliable working solution.
> If i create a fresh Live USB, and set Partition to GPT & target system to UEFI, and then reinstall, would that work ???
Yes, it should work - remember to boot the live session in UEFI mode.

---

### Post by MadMonkey1966 on 2023-05-21
Well, I have installed 2 different versions (22.04 & 23.04), I  thought 22.04 LTS may be better.....but no, everyone ends up with the  same:

**Error 1962: No operating system found, press any key.....**

I  tried MBR & GPT when creating boot media, and installed with F12  UEFI (Not Legacy) boot, no joy. I have run Boot-repair, but does not  seem to solve anything. 
I have removed the Network boot, as that's  all it ever wants to do. It will run the USB time & time again, and  instal fine, but I guess there is some major issue that doesn't want me  to run Linux on it.

Any other ideas would be awesome...  :eek:

---

### Post by tea for one on 2023-05-21
> **MadMonkey1966 said:**
> I  tried MBR & GPT when creating boot media, and installed with F12  UEFI (Not Legacy) boot, no joy. I have run Boot-repair, but does not  seem to solve anything.
There is no need to create GPT on the boot media.
After you have booted into a live session in UEFI mode, open Gparted and create GPT on your [COLOR="#0000FF"]target [/COLOR]disk.

Secondly, in the boot-repair report from post 5:-
[COLOR="#0000FF"]Line 71[/COLOR] - SecureBoot disabled - This system doesn't support Secure Boot.
Secure boot is not new, it's been around for approx 12 years, therefore how old is this PC?

Have you ever updated the UEFI firmware (assuming an update exists)?

---

### Post by oldfred on 2023-05-21
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

Some systems have UEFI that just wants to boot Windows boot entry.
It is possible to just change desciption  of Ubuntu entry to "Windows"
    sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by MadMonkey1966 on 2023-05-24
Sorry for delay in getting back, I have been away for a couple of days.

I have to say I have never used Gparted, so a bit lost there.

I got the computer from itzoo.co.uk a few years back, just so my sister had one. It is nothing flash, but I thought once she didn't need it any more, it would be great for a Linux distro. So I have no idea how old it actually is, i never even thought about updating UEFI firmware (or how to, especially as it does not have an accessible system at present).

Just to add, looking at the BIOS date it is 2012

---

### Post by oldfred on 2023-05-24
Firmware update does not necessarily require an operating system.
Windows usually does it for you.
Linux now can do it for many systems that are newer with fwupdate.

But UEFI is almost an operating system of its own. You can boot into UEFI and check version.
Then go out to vendors web site and its support page and see what latest version is and download it.
Most UEFI then let you then update from a FAT32 formatted partition, either on hard drive or a flash drive.
A few even let you directly update from within UEFI.

---

### Post by MadMonkey1966 on 2023-05-24
Many thanks' tea for one for your time & help, and to you oldfred :):):)

This line above:

**     sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 				**

Solved the issue right away....

I will now do the updates, and all the other stuff to make it as I want it. I think I better leave everything in UEFI as it is now, 
I am paranoid that if I try to update it (if available) it may change what we have just done :D

Don't fix what isn't broken, as they say.....

Thanks both of you once again......
Regards Ian (MadMonkey1966)

---

### Post by tea for one on 2023-05-24
```
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
```
Well, oldfred, another new one for me.
I had no idea that the Windows Boot Manager entry could be tickled like this.
Thank you.

---

### Post by oldfred on 2023-05-24
There are or have been some systems that only want to boot Windows by description "Windows Boot Manager".
But they only check description in UEFI, not actual boot file.
And you can have any description you want for UEFI boot entries. So we make a Windows entry to boot Ubuntu.

---

