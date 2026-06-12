---
title: "Ubuntu boots to EFI Shell"
date: 2023-04-10
forum: Installation &amp; Upgrades
---

### Post by rschamp on 2023-04-10
Hi Everyone,

My little Zotak CI320nano box, which has a dual boot setup (Windows/Ubuntu) died last night while I was using my Plex server. I fear I'll never know if Adam Driver saves that kid from the dinosaurs now. Plex stopped streaming and I checked my machine, it was a black screen with a period on it. So I rebooted and it booted directly to EFI Shell. From EFI Shell I tried reset but it just always boots to the EFI Shell regardless. My SDD no longer appears in the boot options of the bios either which seems weird. Earlier that day Ubuntu prompted me to do a system update, which I did but I don't remember what was updated.

I created a live usb and ran the boot repair tool, pastebin is here: [https://paste.ubuntu.com/p/qGf7MXqsrk/](https://paste.ubuntu.com/p/qGf7MXqsrk/) 

Any help would be appreciated.

---

### Post by yancek on 2023-04-11
See line 21 of boot repair:  "0 OS detected".  It doesn't show any information on sda except that no bootloader is installed on it's MBR.  The UEFI info only shows the builtin shell and sdb (flash drive) options.  Line 58 does show the drive was detected and is 223GB.  If your drive does not show in the BIOS, it may be dead but boot repair did detect it.

Which version of windows did you have installed?  Do you have a live usb of Ubuntu or another Linux OS?  If so, can you boot the Ubuntu live usb and open a terminal and run the 2 commands below and check the output?

```
sudo gparted
sudo fdsik -l
```

---

### Post by tea for one on 2023-04-11
> **rschamp said:**
> So I rebooted and it booted directly to EFI Shell. From EFI Shell I tried reset but it just always boots to the EFI Shell regardless.
When you arrive at the EFI shell, is there any text displayed?
FS0: or FS1: for example?

---

### Post by rschamp on 2023-04-11
Yes, I have a Ubuntu live usb I can use.

fdisk returns: [https://paste.ubuntu.com/p/8qbNtZ82Kt/](https://paste.ubuntu.com/p/8qbNtZ82Kt/)
gaprted  returns: [https://paste.ubuntu.com/p/9jPwrxYppQ/](https://paste.ubuntu.com/p/9jPwrxYppQ/)  (if I hit Ignore  enough times it does open and reports the partition and filesystem as  unallocated)

---

### Post by rschamp on 2023-04-11
This is what I see in efi shell: [https://imgur.com/gallery/bjptM3l](https://imgur.com/gallery/bjptM3l)

---

### Post by tea for one on 2023-04-11
EFI Shell Image:- Missing FS0 probably means that the EFI shell cannot see the EFI partition, consequently the FS (file system) is unavailable.
```
Disk /dev/sda: 223.58 GiB, 240057409536 bytes, 468862128 sectors
Disk model: SATAFIRM   S11  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```
The output above (lines 44 -48) does not show any partitions i.e. sda1,sda2 etc.

Not looking very hopeful at the moment - possible hardware failure?

---

### Post by rschamp on 2023-04-11
Yeah that's where my head's at too. Thankfully it only had the OS and applications on it and data was on an external array.

---

