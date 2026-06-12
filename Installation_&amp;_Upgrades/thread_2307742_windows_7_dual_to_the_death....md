---
title: "windows 7 dual to the death..."
date: 2015-12-28
forum: Installation &amp; Upgrades
---

### Post by z80 on 2015-12-28
ok so after installing windows 7 and lubuntu i seem to be having the exact opposite problem that everyone else has with dual boot.  i forgot how and didnt see smple options to mbr win 7 so its now an uefi drive.  win 7 has somehow made it impossible for grub to be installed over its boot loader.  so i have to go into the bios and select a different partion to boot into lubuntu.  first thing i did once i got into the new install of lubuntu was go to synaptic and installed the (GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)).  but still win7 bootloader dosnt even ask what i want to do it just boots right to windows much to my annoyance.  im starting to wonder if i dont have a efi for windows in the right place and a grub in the wrong placefurther down the drive. its an ssd if that matters.  my last ssd i got it all to work just fine with but that was set an mbr for windows durring installation after several issues with grub.  i tried windows boot repair and the new new grub install. not sure what to do next.

---

### Post by ajgreeny on 2015-12-28
Sounds like a problem that may be solved by running Boot-Repair (see my signature link below).

Run the boot-info script, not the default repair for the moment, and post back here the pastebin link it gives you to a results.txt report file.

---

### Post by z80 on 2015-12-28
> **ajgreeny said:**
> Sounds like a problem that may be solved by running Boot-Repair (see my signature link below).

Run the boot-info script, not the default repair for the moment, and post back here the pastebin link it gives you to a results.txt report file.

[http://paste.ubuntu.com/14255841/](http://paste.ubuntu.com/14255841/)

---

### Post by oldfred on 2015-12-29
See the info at the bottom of Boot-Repair's summary report.

Once you convert to UEFI, best to have all drives as gpt and only boot in UEFI mode.
How you boot install media - flash drive or DVD for both Windows or Linux is then how it installs UEFI or BIOS.
And how you install Windows is how you should install Ubuntu. So if Windows is UEFI, best to install Ubuntu in UEFI boot mode.

Boot-Repair can convert BIOS install to UEFI install. You do not show an Ubuntu entry in the ESP - efi system partition, nor the mount of the /boot/efi/EFI/ubuntu partition in fstab. so you have BIOS boot only.
Boot-Repair just uninstalls grub-pc (BIOS) and installs grub-efi-amd64(UEFI). Entries in UEFI, ESP and fstab are automatically added by grub's UEFI install.

You also show MBR partitioning on 4TB drive which limits it to the 2TiB maximum that MBR(msdos) can support. Best to convert to gpt.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

I have never tried converting, but good backups are required.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by z80 on 2015-12-31
well well, seems this newer bios has options for setting where to boot from in the bios settings itself. just had to point away from windows and to the grub which has windows in it. far easier than my thought of buying another large drive and transfering everything out of the computer to fully efi everything.  its kinda sad that the efi switch hasnt been a little more smooth.  every time i mess with windows and ubuntu together since i got this newer computer, i have had nothing but headaches, mostly because i dont understand efi fully yet. getting there though... thanks for your help. im gonna print this as a pdf for reference the next time i go and redo this computer.

---

