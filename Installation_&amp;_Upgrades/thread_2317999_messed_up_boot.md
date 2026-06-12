---
title: "messed up boot"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by kubbuntu on 2016-03-22
[http://paste.ubuntu.com/15470688/](http://paste.ubuntu.com/15470688/)

Hello everyone. I guess i crashed my previous boot record with windows 10 and kubuntu 14.10. &#305; didn't get back to my boot screen anyhow. so i installed another kubuntu 14.10 beside my previous op.sys.es. now i'm cuious about is there anyway to obtain get back to old boot. that includes kubuntu 14.10 and windows 10.

by the way i tried several attempts which one of them is using boot-repair. but it didnt work well. i guess its because legacy mode issue. Now i cant enter my bios menu. 

&#304; pasted my boot-repair report above. thanks in advance.

---

### Post by oldfred on 2016-03-22
You have an UEFI system.
And Windows and Ubuntu in sda7 are installed in UEFI mode.
But Ubuntu install in sda11 is installed in BIOS/CSM/Legacy boot mode.

UEFI & BIOS are not compatible. You then can only dual boot from UEFI boot menu. Grub only boots systems installed in same boot mode as grub is booted.

Toshiba also now seems to be like some other vendors that modify UEFI to use Description as part of boot. That is not allowed per UEFI standard and of course only valid description is "Windows Boot Manager". 

You should be able to go into UEFI or use one time boot key and boot Windows.
Make sure fast start up is off.

If you boot Boot-Repair in UEFI boot mode, you may need secure boot off but UEFI on in UEFI/BIOS, then it should copy shimx64.efi into /EFI/Boot and rename to bootx64.efi.
If system has fallback or hard drive UEFI entry that will now boot grub/shim. If not we can add an entry.

Reboot installer in UEFI mode and rerun Summary report. Boot-Repairs advanced options can also uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI) to convert sda11 to UEFI boot. But only one Ubuntu install will be in UEFI menu as /EFI/ubuntu. Then from grug you could boot either install or Windows, if all are UEFI.

Details of the work arounds to boot also in link in my signature.

       Toshiba Satellite - turned Secure boot off in Boot-Repair update
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair
[/URL]
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 

[URL="https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair"]
[/URL]

---

### Post by mörgæs on 2016-03-23
14.10 is out of support. 15.10 is a better choice.

---

