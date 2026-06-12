---
title: "Fail Dual Boot"
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by cristoamh on 2018-05-30
Hello Community!

First of all, English isn't my first language so I'm sorry if i have a few mistakes.

This is my problem,  I decided to make a Dual Boot with windows 10 and Ubuntu.([B]NOTE: Windows in one SSD and Ubuntu in another SSD)
[/B]
I've wrote the Note because I think there is the problem, lest continue. After a regular installation of Ubuntu. When I restart my computer, this initializes directly Ubuntu, but here is also instaled Windows, and the only form to Change to windows or vice versa is changing the boot loading pressing F12, If I don't press something this initialize Ubuntu.

When I did the installation I make a uefi partition, a swap partition and a root partition. And also selected the boot in the windows SSD.

What can I do?

EDIT:
Don't know if this helps but I used boot-repair to get a report: [http://paste.ubuntu.com/p/5Jkmd6Hb9j/](http://paste.ubuntu.com/p/5Jkmd6Hb9j/)
Thanks for the help!

---

### Post by oldfred on 2018-05-31
You have new UEFI system.
But your Windows install is in the now 35 year old BIOS/MBR configuration.
Windows on new systems requires UEFI/gpt (since 2012), but still can be installed in the old configuration for backwards compatibility on older hardware. Windows 7 default install is BIOS/MBR but installer can be copied to flash drive and easily converted to UEFI installer.

How you boot install media UEFI or BIOS/Legacy/CSM, both Windows & Ubuntu is then how it installs.

UEFI and BIOS are not compatible. They write hardware data to drive differently for operating system. Or you can only dual boot directly from UEFI boot menu, and grub can only boot other systems installed in same boot mode as Ubuntu/grub is installed.

Ubuntu can boot in BIOS boot mode from gpt drive, so you do not have to reinstall. Just shrink ESP, sda1 by 4 or 5 MB and create a new unformatted 1 or 2MB partition with the bios_grub flag.
Then boot Ubuntu installer in BIOS mode, add Boot-Repair and run the full uninstall/reinstall of grub to install the BIOS version of grub.

If you just installed Windows, better to reinstall in UEFI mode, but easier to convert Ubuntu. Keep Ubuntu drive as gpt with ESP - efi system partition so later you can easily convert back to UEFI.

Note that newer Windows with fast start up will turn that back on with updates. Then grub will not boot Windows and you have to directly boot Windows from BIOS (UEFI) to be able to turn fast start up back off.

---

