---
title: "One snowball after another"
date: 2017-12-28
forum: MINT
---

### Post by techlikeagirl on 2017-12-28
I've used Linux Mint for a few years, I was using it on a POS Toshiba, then about 2 months ago I bought a Dell Latitude E6410, just swapped my hard drive from the former to the latter. Occasionally when I booted, it would blank out upon booting with some error that I never got to investigating, with a "grub rescue message". I would hit the power button, restart, get the "your machine did not shut down properly, which option do you want" then i would choose my Mint 18 and be on my way.

Fast forward to the 18.3 Mint update, chose to update because why wouldn't I, restarted my computer, got to the grub rescue message. I hit the power button, restarted, and this time, back to grub rescue. I've read these forums, tried the boot-rescue everything, no go. I get the "file '/grub/i386-pc/normal.mod" not found, I have searched my file system, found it. I discovered my new(er) laptop may be compatible with UEFI, but when I tried to install Linux under that, I get a root file system not specified error. I've tried the ins normal.mod code, no go. It's been over a week with banging my head against a wall trying to get my OS working again. 

I've been able to work normally with the Mint 17 boot cd, but I view that as an emergency, and tedious. 

Here's the link to the boot-repair pastebin: [http://paste.ubuntu.com/26274110/](http://paste.ubuntu.com/26274110/)

---

### Post by Irihapeti on 2017-12-28
Thread moved to ***MINT*** subforum.

---

### Post by oldfred on 2017-12-28
Moved to Mint sub-forum.

Do not know all the differences of Mint vs. Ubuntu.

But in general UEFI requires gpt partitioning.
Report say UEFI Secure Boot may be on. That has to be off to boot in BIOS mode, and if installing proprietary drivers also must be off. 

If only installing Linux you can use gpt and boot in either UEFI (if you have ESP), or in BIOS boot mode (if you have bios_grub partition).
Windows only boots in UEFI mode from gpt partitioned drives.

For more info on UEFI installs, see link below in my signature.

---

### Post by techlikeagirl on 2017-12-28
I went back into BIOS to double check my settings, Legacy was chosen over UEFI. I do not see any other settings for disabling secure boot (yes I checked all of the settings to see if the option was hidden). Upon restart I ran in the terminal: sudo parted -l
Model: ATA WDC WD3200BPVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  316GB  316GB   primary   ext4            boot
 2      316GB   320GB  4156MB  extended
 5      316GB   320GB  4156MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: TSSTcorp DVD+-RW TS-U633J (scsi)
Disk /dev/sr0: 1383MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac

Number  Start  End     Size    File system  Name   Flags
 1      8192B  24.6kB  16.4kB               Apple
 2      115MB  124MB   9306kB               EFI

---

### Post by oldfred on 2017-12-28
Many systems call the UEFI Secure Boot "Windows" or "Other". 
And then the fine print says if using Windows 7 use "Other". As Windows 7 does not support Secure Boot.

---

