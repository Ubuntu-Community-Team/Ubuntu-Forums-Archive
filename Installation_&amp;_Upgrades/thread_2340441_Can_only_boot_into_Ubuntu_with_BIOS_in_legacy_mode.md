---
title: "Can only boot into Ubuntu with BIOS in legacy mode, and only when a USB is inserted"
date: 2016-10-18
forum: Installation &amp; Upgrades
---

### Post by brutikk on 2016-10-18
I have recently botched a fresh install of Ubuntu 16.10 on my machine.  Previously, I was dual booting Ubuntu Mate 15.10 and Windows 10.

When installing Ubuntu 16.10 from a USB, I came across various warnings (such as a warning that I might not be able to boot into Windows because it is non-UEFI).

When I do not have my boot-repair-disk USB inserted in my machine, my computer will boot into a built-in recovery tool -- despite me trying to boot into Ubuntu.  If I insert my boot-repair-disk USB, I can try and boot in to it, but that boot will fail.  Instead, I get booted into my Ubuntu installation.

My goal is to be able to dual boot Windows 10 and Ubuntu 16.10.  I would like to clean up all of the unnecessary partitions as well (the windows 7 partitions are still there for reasons unknown to me), but the primary goal is being able to boot into Windows or Ubuntu without having to go through my USB. Any advice on how to proceed is appreciated.

Output from boot-info-script can be found here: [http://pastebin.com/BgZrqWX5](http://pastebin.com/BgZrqWX5) (the attachment was too large to include in my post)

---

### Post by oldfred on 2016-10-18
You have what looks like a BIOS boot version of Windows in sda3, but drive is gpt partitioned.
Windows only boots in UEFI mode from MBR partitions and only in UEFI mode from gpt partitioned drives.

With UEFI Window also has several extra partitions and would have boot files in the ESP - efi system partition for UEFI. You have neither.

Perhaps forcing the UEFI install of Ubuntu and ignoring warning messages is why drive was converted from MBR to gpt. You are lucky to still have Windows install as many conversion totally erase & redo drive.

You are not specifically showing Windows 10, but older script just parses what was available back when last updated. Boot-Repair uses a newer fork of bootinfoscript and can also do repairs. Windows 10 would have installed to the Windows 7 partitions, so older script may not show correct version.

But you may need to totally reinstall. You may be able to convert back to BIOS/MBR, but must have really good backups as any conversion has risks.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

But having new UEFI hardware and running the 35 year old BIOS/MBR configuration in emulation probably is not best option. But since it has been around for so long it is well known. 

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

