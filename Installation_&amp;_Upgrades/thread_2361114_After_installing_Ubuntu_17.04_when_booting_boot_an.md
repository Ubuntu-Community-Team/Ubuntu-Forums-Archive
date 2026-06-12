---
title: "After installing Ubuntu 17.04 when booting boot and select proper boot device"
date: 2017-05-12
forum: Installation &amp; Upgrades
---

### Post by wristymeat on 2017-05-12
I've been trying to install ubuntu on a fresh hdd and am a brand new user who does not understand Linux very well yet.  Every time I install ubuntu I run into the same error " reboot and select proper boot device or insert boot media in selected boot device and press a key".  I've been attempting to solve my problem via the forums and and have had no luck. Please help.
Also I am booting from a Gateway Dx4870-ub318
I've tried : reordering my boot order and using boot-repair.
After I use boot repair I get these error messages before it displays the original error "reboot and select proper boot device or insert boot media in selected boot device and press a key"
     -failed to open /EFI/BOOT/mmx64.efi - Not Found
     -failed to load image /EFI/BOOT/mmx64.efi - Not Found
     -failed to start MokManager: Not Found
     -failed to open /EFI/BOOT/grubx64.efi - Not Found
     -failed to load image /EFI/BOOT/grubx64.efi: Not Found
     -start_image() returned Not Found
Here is my paste bin: [http://paste.ubuntu.com/24562251/](http://paste.ubuntu.com/24562251/)
Any help is greatly appreciated.

---

### Post by coffeecat on 2017-05-12
Support, not a Forum Feedback & Help thread.

*Thread moved to **Installation & Upgrades**.*

---

### Post by gordintoronto on 2017-05-13
I don't know for sure, but the problem might be that you have formatted the drive as GUID.

---

### Post by oldfred on 2017-05-13
You have grub installed both for BIOS boot to gpt's protective MBR and to ESP for UEFI boot.
And since fstab shows mount of efi partition, you system is configured for UEFI boot.

How you boot installer or repair flash drives UEFI or BIOS is how it works, installs, or repairs. So always boot in same mode, UEFI in your case.
BIOS boot will try to load grub in MBR and that will fail.

Boot-Repair also added 25_custom as it saw a lot of .efi boot files and adds then to grub menu. You may not need all or any of them.

```
BootOrder: 0004,0005,0000,0002
Boot0000  ubuntu	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002  Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0004* UEFI: ST1000DM010-2EP102	PciRoot(0x0)/Pci(0x1f,0x2)/Sata(1,65535,0)/HD(1,GPT,f9cc5353-9e4f-4d57-8f86-4df284e01077,0x800,0x94f800)AMBO
Boot0005  UEFI: KingstonDataTraveler 3.0PMAP	PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(2,0)/HD(1,MBR,0x116,0x2f9770,0x1200)AMBO

```

You want to be booting from UEFI entry 0000 or ubuntu, but it is now 3rd in boot menu.
Not sure what UEFI key is used to choose boot entries, but often f10, f12 or f8, but check your manual.

The files shown as errors are in /EFI/ubuntu not /EFI/Boot. But I do have them in both places and no errors, so related to your UEFI??
Normally we copy /EFI/ubuntu/shimx64.efi to /EFI/Boot and rename to bootx64.efi as a fallback or hard drive boot entry for those systems that do not directly boot an ubuntu entry. Those systems violate UEFI standard that says NOT to use description as part of boot. And only valid description is "Windows Boot Manager". If only booting Ubuntu another work around is to in effect change description of ubuntu boot to Windows boot, and really boot shimx64.efi. UEFI checks description not actual boot file.

More details on the work arounds in link in my signature & these:
       Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
[http://askubuntu.com/questions/235567/windows-8-removes-grub-as-default-boot-manager](http://askubuntu.com/questions/235567/windows-8-removes-grub-as-default-boot-manager)

---

