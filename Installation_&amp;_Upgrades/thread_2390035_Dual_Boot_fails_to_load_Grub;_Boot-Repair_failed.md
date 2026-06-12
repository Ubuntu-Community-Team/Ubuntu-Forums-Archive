---
title: "Dual Boot fails to load Grub; Boot-Repair failed"
date: 2018-04-24
forum: Installation &amp; Upgrades
---

### Post by gregoledra on 2018-04-24
Hello!

[FONT=arial]Boot-Repair pastebin (prior to trying without secure boot):[/FONT]
[FONT=arial][http://paste.ubuntu.com/p/PbFcVHFqKr/](http://paste.ubuntu.com/p/PbFcVHFqKr/)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]**GOAL:**[/FONT]
[FONT=arial]Access Ubuntu on /dev/sda5 and /dev/sda6 via dual boot (aka just get grub to appear)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]**Method:**[/FONT]
[FONT=arial]Installed Ubuntu on HDD - success; failed to boot there.[/FONT]
[FONT=arial]Installed Ubuntu on SSD (preferred) - success; failed to boot there.[/FONT]
[FONT=arial]Modified bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi - successful edit; failed to boot into Ubuntu[/FONT]
[FONT=arial]Ran efibootmgr off of a USB Linux installation; changes did not take, currently does not show Ubuntu as being in the boot order at all[/FONT]
[FONT=arial]Verified all OS's are installed in UEFI mode (unable to boot into anything except USB in Legacy)[/FONT]
[FONT=arial]Attempted to change boot order in the BIOS-like screen at startup. Changing boot order has no effect - it doesn't even make booting off of a USB automatic. Instead it always boots directly to Windows.[/FONT]
[FONT=arial]Attempted to run Boot-Repair (see output above)
Disabled Secure Boot
Modified bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi - successful edit; failed to boot into Ubuntu
Ran efibootmgr off of a USB Linux installation; changes did not take, although ubuntu is a listed option @ 000A, Windows Boot Manager is always above it.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]**Time put in:**[/FONT]
[FONT=arial]A day (~10 hours)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]**Notes:**[/FONT]
[FONT=arial]Hitting F12 allows for seeing a USB and Windows Boot Manger on the HDD and SSD separately (so 3 entries total), but Grub/Ubuntu has never showed up
My system is using UEFI[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]**Intended Resolution I can't do:**[/FONT]
[FONT=arial]I assume that fixing the boot order will solve the problem, yet since the changes I make when booting to a USB don't seem to be saved after restarting and changing the Windows bcdedit configuration path didn't work and changing the UEFI boot order in the BIOS-like startup screen has no effect, I don't know what to do.

[B]Questions
[/B]Is there a way to set grub as the default in Windows without using bcdedit?
Is there a reason why \EFI\ubuntu\grubx64.efi doesn't work?
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any help would be appreciated. I am currently going to try setting \sda1\EFI\ubuntu\shimx64.efi in Windows instead of \EFI\ubuntu\shimx64.efi and then try \sda1\EFI\ubuntu\grubx64.efi[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks for any help you can give me![/FONT]

---

### Post by gregoledra on 2018-04-24
Hey I got it!
I re-ran:[FONT=arial] bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi[/FONT]
And rebooted twice (perhaps it wasn't set until after the first boot).

---

### Post by oldfred on 2018-04-24
I see Acer mentioned.
Is this an Acer and what model?

If Acer (all models as far as I know) you have to set UEFI password and enable "trust" on the Ubuntu/grub .efi boot files from within UEFI.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="https://ubuntuforums.org/showthread.php?t=2358003"]https://ubuntuforums.org/showthread.php?t=2358003
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 

Some older models have needed updates to UEFI from Acer. Old threads on trust mention downgrading UEFI, but newer threads say newest UEFI from Acer works. But that was last year, so may depend on version of UEFI you have from Acer.

[URL="https://ubuntuforums.org/showthread.php?t=2358003"]
[/URL]

---

