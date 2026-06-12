---
title: "Dual-boot with Windows 10 and Ubuntu 19.04 on Dell XPS 13 not working"
date: 2019-09-07
forum: Installation &amp; Upgrades
---

### Post by gabbeee on 2019-09-07
Hi,

I am quite new to Linux and this is my first post here. I'd be glad for some help!

I can't get dual boot to work on my Dell XPS 13 (9360). I have the latest BIOS version; 2.12.0. I had Windows 10 installed and first turned off Bitlocker-encryption, then repartitioned my hardisk to make space for Ubuntu with AOMEI Partition Assistant. After that I made a USB with Ubuntu 19.04 and installed Ubuntu (alongside Windows). When booting I go directly into Windows and I don't get the option to choose between Windows and Ubuntu. I understand that this has something to do with how Grub is set up. 

I've tried solving it by following other threads with problems like this, but I ended up having to re-install Windows then trying to install Ubuntu alongside it. But the problem is still the same.

I've checked and ensured that my BIOS settings are (acording to suggestions in other threads):

 * Secure boot disabled.
 * In section POST behaviour: Fastboot, selected Thorough boot.
 * In section General: Advanced Boot Options, enabled Legacy Option ROMs and enabled UEFI Network Stack.
 * In section System Configuration: SATA Operation, selected AHCI.

I've also tried the command in the Windows Command Prompt:
```
[COLOR=#242729][FONT=Consolas]bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi[/FONT][/COLOR]
```
But I still don't see a Grub menu and it boots directly into Windows.

/Gabriel

---

### Post by Rubi1200 on 2019-09-07
Hi and welcome to the forums :-)

Please use the live Ubuntu image to boot the computer and run the boot info summary report (first link in my signature).

The report will help us diagnose the problem and allow us to offer suggestions to fix things.

Please note, only run the report do not attempt to repair until someone has reviewed the report.

Good luck!

---

### Post by gabbeee on 2019-09-07
Thanks for the quick reply!

Here is the url to my boot info: [http://paste.ubuntu.com/p/v4qz3HhWqr/](http://paste.ubuntu.com/p/v4qz3HhWqr/)

---

### Post by ubfan1 on 2019-09-07
It's the Windows Settings Power option (really hidden under Advanced..., Additional controls... blah.. blah...) that you want to be sure is off, or hibernation is used to shutdown, and the "boot" is skipped entirely, as Windows is restored from hibernation.

---

### Post by gabbeee on 2019-09-07
Thanks for the tip, but it didn't help. I first turned off hibernation at shutdown and then I also turned off hibernation completely in Windows.

---

### Post by oldfred on 2019-09-07
You show a Bios Boot partition which is also know as bios_grub. That is only used with BIOS boot installs of Ubuntu onto gpt partitioned drives.
Windows only installs to gpt with UEFI, but Ubuntu will let you install in BIOS boot mode (maybe it should not).

You also booted live installer to run Boot-Repair in BIOS mode. You need to boot in UEFI mode.
You should have two boot options for flash drive installer if Secure Boot is off. You may have to turn on allow full USB access or USB boot to get UEFI boot option.

From Boot-Repair's advanced options booted in UEFI mode, you can to a total reinstall of grub, which will uninstall the BIOS version & install the UEFI version of grub.

       Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)

---

### Post by gabbeee on 2019-09-07
Thanks a lot!

I did exactly as oldfred wrote and did a boot-repair. Now I can see grub when I boot and dual-boot just fine.

I can't believe I missed that there were two boot-options! I just chose the first one as I didn't even see the other!

Here is the boot-info result after the repair: [http://paste.ubuntu.com/p/zgy6nbh3k9/](http://paste.ubuntu.com/p/zgy6nbh3k9/)

Thanks again for the help everyone!

---

### Post by oldos2er on 2019-09-08
Would you please mark your thread as "Solved" under Thread Tools at the top of the page? It's a courtesy to other users who're looking for answers to this same question. Thanks.

---

