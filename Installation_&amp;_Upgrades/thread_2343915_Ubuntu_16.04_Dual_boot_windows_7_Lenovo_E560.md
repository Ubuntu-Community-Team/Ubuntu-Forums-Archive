---
title: "Ubuntu 16.04 Dual boot windows 7 Lenovo E560"
date: 2016-11-20
forum: Installation &amp; Upgrades
---

### Post by anderskitson2 on 2016-11-20
Hi,

I have installed Ubuntu 16.04 via a usb flash drive and it seems to have had a successful installation. 
However It only boots into Windows and there is no Grub menu to choose OS's.
I ran Boot Repair and got this output

[http://www.paste2.org/8BtwvLHz](http://www.paste2.org/8BtwvLHz)

Here is the first portion which can be viewed in full in the link

```

    Boot Info Script cfd9efe + Boot-Repair extra info [Boot-Info 26Apr2016]


    ============================= Boot Info Summary: ===============================

    => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector
    221345792 of the same hard drive for core.img. core.img is at this
    location and looks for (,gpt7)/boot/grub. It also embeds following
    components:

    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
    => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

    sda1: __________________________________________________ ________________________

    File system: vfat
    Boot sector type: Windows 8/2012: FAT32
    Boot sector info: No errors found in the Boot Parameter Block.
    Operating System:
    Boot files: /EFI/Boot/bootwinre.efi /EFI/Boot/bootx64.efi
    /EFI/Boot/lenovobt.efi
    /EFI/Microsoft/Boot/bootmgfw.efi
    /EFI/Microsoft/Boot/bootmgr.efi
    /EFI/Microsoft/Boot/memtest.efi

    sda2: __________________________________________________ ________________________

    File system:
    Boot sector type: -
    Boot sector info:
    Mounting failed: mount: unknown filesystem type ''

    sda3: __________________________________________________ ________________________

    File system: ntfs
    Boot sector type: Windows 8/2012: NTFS
    Boot sector info: No errors found in the Boot Parameter Block.
    Operating System:
    Boot files: /bootmgr /Boot/BCD /Windows/System32/winload.exe

    sda4: __________________________________________________ ________________________

    File system: BIOS Boot partition
    Boot sector type: Grub2's core.img
    Boot sector info:

    sda5: __________________________________________________ ________________________

    File system: ntfs
    Boot sector type: Windows 7/2008: NTFS
    Boot sector info: No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

    sda6: __________________________________________________ ________________________

    File system: ntfs
    Boot sector type: Windows 8/2012: NTFS
    Boot sector info: No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

    sda7: __________________________________________________ ________________________

    File system: ext4
    Boot sector type: -
    Boot sector info:
    Operating System: Ubuntu 16.04.1 LTS
    Boot files: /boot/grub/grub.cfg /etc/fstab
    /boot/grub/i386-pc/core.img

    sda8: __________________________________________________ ________________________

    File system: swap
    Boot sector type: -
    Boot sector info:

    sdb1: __________________________________________________ ________________________

    File system: vfat
    Boot sector type: SYSLINUX 6.03
    Boot sector info: Syslinux looks at sector 32800 of /dev/sdb1 for its
    second stage. The integrity check of Syslinux failed.
    No errors found in the Boot Parameter Block.
    Operating System:
    Boot files: /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi
    /EFI/BOOT/grubx64.efi /ldlinux.sys
```

---

### Post by QIII on 2016-11-20
Hello!

When posting output from terminal commands, please do not include extra formatting.  To post such information, you may do one of three things:

1.  Click on the # symbol above the text entry box, place your cursor between the code tags and add your text.

2.  Add your text, highlight it and click the # symbol.

3. Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after.  The square brackets are required.

Thanks.

---

### Post by oldfred on 2016-11-20
You have UEFI hardware and Windows installed in UEFI boot mode.
But you installed Ubuntu in the 35 year old BIOS boot mode, now emulation using CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

You also booted live installer in BIOS boot mode to run Boot-Repair.
Best to always boot in UEFI mode since system is UEFI.
And how you boot is then how systems install, both Windows & Ubuntu.

Boot-Repair can convert your BIOS install to UEFI, in advanced mode if booted in UEFI mode.
It uninstalls grub-pc and installs grub-efi-amd64.

But some systems do not like to boot anything but Windows in UEFI mode and then need work arounds. Often copying some boot files.
[https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments](https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments)
Lenovo Linux support - many obsolete versions of Linux
[https://support.lenovo.com/us/en/documents/pd031426](https://support.lenovo.com/us/en/documents/pd031426)
 Warning: Microsoft Signature PC program now requires that you can't run Linux. Lenovo Yoga 900 ISK2 UltraBook Sept 2016
[URL="https://ubuntuforums.org/showthread.php?t=2337719"]https://ubuntuforums.org/showthread.php?t=2337719

      [/URL]T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) [URL="https://ubuntuforums.org/showthread.php?t=2337719"]
[/URL]

---

### Post by anderskitson2 on 2016-11-20
Ok, sounds like a lot, but it's worth it to get Linux running on this laptop. 
How would I boot the live usb into UEFI mode? Do I need to change something in the BIOS?
I think I checked the BIOS and UEFI was the default boot mode.

---

### Post by Dennis N on 2016-11-20
> How would I boot the live usb into UEFI mode? Do I need to change something in the BIOS?
No, you need the one-time boot menu to come up when booting by pressing the special key during start up. Your installler USB should show two entries, one with UEFI in the description - for example, mine will show **(UEFI) Kingston Data Traveler**, and **Kingston Data Traveler**. Use the first one.

---

