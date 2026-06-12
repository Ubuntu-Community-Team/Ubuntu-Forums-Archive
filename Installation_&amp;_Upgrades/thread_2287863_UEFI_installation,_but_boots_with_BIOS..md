---
title: "UEFI installation, but boots with BIOS."
date: 2015-07-22
forum: Installation &amp; Upgrades
---

### Post by Antoan_Dimitrov on 2015-07-22
Hello, 

I have just installed Ubuntu MATE and during the installation I created those partitions:

1) EFI Partition - 200 MB
2) root partition - 20 GB
3) home partition - 120 GB 
4) swap partition - 6 GB
5) NTFS partition - 500 GB

The installation went fine, but when I rebooted the UEFI couldn't boot, it had nowhere to boot from.
Then I went in BIOS and changed from UEFI to Legacy Boot and it booted fine.

Why did that happen?

Thank you,
Antoan Dimitrov

---

### Post by oldfred on 2015-07-22
How you boot installer i show it installs. So if you boot USB flash drive in CSM/Legacy/BIOS mode it installs in BIOS boot mode.

Is drive gpt partitioned?

If drive is gpt and you have the efi partition set to be seen as ESP- efi system partition then you can use Boot-Repair to convert from BIOS to UEFI. But all Boot-Repair really does it uninstall grub-pc(BIOS and install grub-efi-amd64(UEFI) which also adds efi partition to fstab and a few other things.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Antoan_Dimitrov on 2015-07-22
[http://paste.ubuntu.com/11923004/](http://paste.ubuntu.com/11923004/)

Obviously, GRUB2 boots the OS, but I made and EFI partition during installation.
What should I do, because while I am loading the OS, it gives some errors before it boots?

---

### Post by oldfred on 2015-07-22
It looks like you booted Boot-Repair in BIOS mode. Did you run it from inside your install?
Not sure if then it still has in advanced options the choice to totally uninstall grub-pc and install grub-efi-amd64.

Also I do not see the bios_grub partition. Normally grub does not install to gpt partitioned drives unless you have a bios_grub for BIOS boot. And it is showing the /boot/efi mount in fstab which normally is only for UEFI boot?

Errors may be from UEFI, grub or Ubuntu. Often UEFI gives messages if booting in BIOS mode. 
What are error messages?

Some brands also require work arounds for UEFI boot.
What brand/model system?

---

### Post by Antoan_Dimitrov on 2015-07-22
I have not run boot-repair at all.
Ubuntu was supposed to boot with UEFI, but I do not know why, when booting, UEFI does not find any bootable devices. This is why there is /boot/efi, but not bios_grub. However when I change settings from BIOS to use Legacy Boot it boots up, however with those errors:

first:
ACPI PCC probe failed.
starting version 219

then something like that:
[drm:intel_set_cpu_fifo_underrun_reporting] *ERROR*
[drm:intel_pch_fifo_underrun_irq_handler] *ERROR*
Then Ubuntu loads normally. 

The machine is Acer Aspire E1-531G.

---

### Post by grahammechanical on 2015-07-22
Just so we do not get distracted.

The system messages "ACPI PCC probe failed" & "Starting version 219" began appearing during the loading of Linux while Ubuntu 15.04 was still in its 26 week development period. They are nothing to worry about. They will not be present in 15.10. Version 19 refers to the veriosn of SystemD that is being loaded. SystemD is used to start and stop system services. Ubuntu started using SystemD during the devlopement of 15.04.

I say nothing about the other two messages.

Regards.

---

### Post by Antoan_Dimitrov on 2015-07-22
Yes, just fixed those messages.
They were appearing because of the graphics card. I changed the driver and they disappeared.
It seems to be working smooth now using GRUB. What should I do? Should I remove GRUB and install UEFI because there is an EFI partition?

Thanks

---

### Post by oldfred on 2015-07-22
Acer is one that requires you to set an UEFI password (never lose that) and set trust. I then allows added settings.

       Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot
[/URL]
 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]
[/URL]

---

### Post by Antoan_Dimitrov on 2015-07-23
Thanks!

---

