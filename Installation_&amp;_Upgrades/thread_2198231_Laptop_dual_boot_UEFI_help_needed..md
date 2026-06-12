---
title: "Laptop dual boot UEFI help needed."
date: 2014-01-07
forum: Installation &amp; Upgrades
---

### Post by manthony121 on 2014-01-07
I am trying to get Ubuntu 12.04.3 LTS x86_64 running on my Toshiba Satellite C55D-A5381 laptop.  The laptop uses an AMD E1-1200 APU with Radeon graphics.  Relevant BIOS settings are: Boot Speed: [Fast|Normal]; Bood Mode: [UEFI|CSM]; Secure Boot [Enable|Disable].  It came with Win8 pre-installed.  I used the Windows Disk Management program to shrink the main NTFS partition, and installed Ubuntu 12.04 (64 bit).  Once that was done, the system would boot Win8 from the grub menu if the BIOS were set to UEFI, and Ubuntu from the grub menu if the BIOS were set to CSM.  In either case (UEFI or CSM), I would get the grub menu, but, if I selected Ubuntu while UEFI was selected, I would just get a purple screen, with no further progress.

The situation changed with the last set up upgrades.  At the first re-boot, with upgrades applied, and CSM boot mode selected in BIOS, I got the "error:invalid arch independent ELF magic" message, followed by the "grub rescue>" prompt.  An "ls" command gives: "(hd0) (hd0,gpt9) ....(hd0, pgt1)"  The error message appeared before getting to the grub menu screen.  If I switched to UEFI boot, I got the grub menu, from which Windows boots, but Ubuntu leaves me with an eternal blank, purple screen.  Selecting a recovery entry leads to a text listing of the boot process, that eventually stops (not in the same place every time).  The only thing in the dmesg listing that looks out of the ordinary is the line: "ACPI warning 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI).SMBS.SMB0 1 (20121018/"   Booting to an earlier kernel: same effects.  The current kernel is 3.8.0-35-generic.

I put in a USB stick with 12.04.3 x64 on it.  Booting from that gives a blank (non-purple) screen in UEFI mode.  In CSM mode, it boots to the USB version Ubuntu.

Trying to boot with BIOS "Secure Boot" enabled: Boot failure: a proper digital signature was not found

I have tried the "nomodeset" and "acpi_osi=" kernel options, but no joy.

It doesn't seem to be a grub issue, as the menu comes up OK, with the heading: Grub version 1.99-21ubuntu3.10.  Just before the grub menu appears, this information appears very briefly:

Failed to open \EFI\Microsoft\Boot\grubx64.efi - 800000000000000E
Failed to load image
Failed to open \EFI\Microsoft\Boot\MokManager.efi - 800000000000000E
Failed to load image
Could not open "\EFI\BOOT\fallback.efi": 14
Failed to open \EFI\BOOT\grubx64.efi - 800000000000000E
Failed to load image
Failed to open \EFI\BOOT\MokManager.efi = 800000000000000E
Failed to load image
error: efidisk read error.

Once booted from a USB stick, here is the partition info:

Model: ATA TOSHIBA MQ01ABF0
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number...Start.......End.......Size........File system......Name.......................Flags
.1...........1049kB...1075MB..1074MB..ntfs.................Basic data partition....hidden, diag
.2...........1075MB..1347MB..273MB....fat32...............Basic data partition....boot
.3...........1347MB..1482MB..134MB....ntfs.................Basic data partition....msftres
.4...........1482MB..159GB....157GB....ntfs.................Basic data partition
.6...........159GB....209GB....50.0GB...ext4
.7...........209GB....480GB....271GB....ext4
.8...........480GB....488GB....8001MB..linux-swap(v1)
.9...........488GB....488GB....1049kB..........................................................bios_grub
.5...........488GB....500GB....11.9GB...ntfs..................Basic data partition....hidden, diag

I would appreciate any advice on how to proceed.

---

### Post by oldfred on 2014-01-07
Once you start booting in one mode either UEFI or BIOS you cannot switch to another, or grub menu does not work. You should be able boot from UEFI/BIOS menu but may have to turn on UEFI or CSM for install in that mode.
Best to convert Ubuntu to UEFI boot.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by manthony121 on 2014-01-09
[http://paste.ubuntu.com/6723744/](http://paste.ubuntu.com/6723744/)

I did NOT try the auto-repair option.

---

### Post by oldfred on 2014-01-10
It looks like you converted Ubuntu to UEFI boot from BIOS boot. Leave secure boot off, but have UEFI on.
Can you boot an ubuntu entry in UEFI menu. And boot the Windows entry.
And boot Windows from grub menu?

It does also look like you booted Boot-Repair in BIOS mode. You need to consistently boot in UEFI mode. UEFI menu should give you two choices one UEFI and the other without UEFI.
This shows both screens so you know which way you booted.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by manthony121 on 2014-01-12
The problem is that I cannot boot Ubuntu in UEFI mode.  I get the "Grub version 1.99-21ubuntu3.10" menu, from which I select "Try Ubuntu".  After that, the screen goes black, and nothing (visible) happens.  I cannot switch to an alternate console with "Ctrl-Alt-F1", nor can I reboot with a "Ctrl-Alt-Del", "Ctrl-Alt-Bksp", or "Ctrl-Alt-Esc".  The only way to recover is to hold down the power button until the machine shuts off.  I have tried adding "nomodeset" and "acpi_osi=" to the boot command, with no effect.

---

### Post by manthony121 on 2014-01-12
Another curious event: when I try to boot Ubuntu from the USB, in UEFI mode, instead of just getting a black screen it will, on occasion, give a black screen that then starts to "bleed" white color from the edges, eventually turning the entire screen slowly white, from which it then changes slowly to grey.  The whole process takes about 30 seconds or so, and only happens once in a while.  Any idea what that's about?

FWIW, I also tried buring in the 12.04.3 LTS 64 bit iso image to a DVD, but it won't boot from that, either.

---

### Post by oldfred on 2014-01-12
You are booting, but it seems like video issues or perhaps other boot parameters. I do not know AMD but this may work. On grub menu press e, scroll to linux line, replace quiet splash with nomodeset.

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Also this one:
radeon.modeset=0

---

### Post by manthony121 on 2014-01-14
Problem solved: I had to add "acpi_backlight=vendor" to the boot command line.  I *never* would have found that on my own. Thanks for the help, everyone!

---

