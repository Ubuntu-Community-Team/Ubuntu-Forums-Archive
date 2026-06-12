---
title: "Is it possible to install grub without reinstalling?"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by stoopkitty on 2010-12-22
I have an iMac with ubuntu on it but I recently partitioned my drive, hoping to dual boot, and installed Mac OS but when I installed, it changed the bootloader so that it only booted up in Mac. To fix this, I installed rEFIt which is a bootloader that let's you choose which os to boot into. This kind of worked but it would not boot into ubuntu because, as I found from  [this thread]("http://ubuntuforums.org/showthread.php?p=10266209#post10266209"), ubuntu needs grub installed. In that thread, the suggestion to get grub installed is to do a clean install, wiping out my current filesystem. I was wondering if there was any way to install grub without wiping out my filesystem and having to do a clean install?

If there isn't, what is the best way to back up to ensure that I can keep all of my settings and files?

---

### Post by Quackers on 2010-12-22
You won't be able to follow normal guides for re-installing Grub because you will have a GUID partition table, having a Mac.
I honestly don't know whether you can install grub to the rEFIt partition or whether you will need a separate boot partition, so I would urge caution.
There is a user here who knows all about this kind of thing. In fact he has a web site that deals with this kind of thing.
I have asked him to pay this thread a visit, but it could be a while as he isn't usually online until later on.

---

### Post by stoopkitty on 2010-12-22
thanks. if it's yugnip, i feel bad about bothering him because i posted a thread before which he helped me on.

Also i found [this thread]("http://ubuntuforums.org/showthread.php?t=1549174") which might help but i'm not exactly sure if that is my problem.

EDIT: Here is the partiton scheme thing that partition inspector (a utility that comes with refit) gave me, i'm not completely sure what it means but it might help:



```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1           2048         4095  GRUB2 BIOS Boot
 2           4096    390636539  Basic Data
 3      390636544    391046143  EFI System (FAT)
 4      391047168    964546559  Mac OS X HFS+
 5      964808704    976773119  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1         2047  ee  EFI Protective
 2           2048         4095  c0  Unknown
 3 *         4096    390636539  83  Linux
 4      390636544    391046143  ef  EFI System (FAT)

MBR contents:
 Boot Code: GRUB

Partition at LBA 2048:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 1, type GRUB2 BIOS Boot
 Listed in MBR as partition 2, type c0  Unknown

Partition at LBA 4096:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 2, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 390636544:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 3, type EFI System (FAT)
 Listed in MBR as partition 4, type ef  EFI System (FAT)

Partition at LBA 391047168:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+

Partition at LBA 964808704:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap
```

---

### Post by Quackers on 2010-12-22
No, I wasn't referring to yugnip.
Unless it's absolutely necessary for some reason, I wouldn't recommend downgrading grub2 to grub legacy.
I honestly don't know whether that would work for your system. I'm not sure you have an mbr as such. You may have a hybrid mbr, but I'm not certain.

---

### Post by srs5694 on 2010-12-23
Yes, that's a hybrid MBR; the definition of a hybrid MBR is a disk with valid GPT data, and an MBR that contains both a type-0xEE partition and at least one other partition. That's what's shown in the posted output.

Booting Macs in a dual-boot configuration can be a bit tricky, since Ubuntu has poor support for this configuration. My own recommendation would be to install GRUB 2's *EFI* version. In Ubuntu, this is in the grub-efi package, rather than the more common grub-pc version. This will enable you to convert the hybrid MBR into a conventional GPT, which is much safer. (Hybrid MBRs violate the GPT standard and are the source of many problems.) Installing anything in Linux could be tricky if you can't get it booted, though. (Have you tried [Super GRUB Disk?](http://www.supergrubdisk.org)) If there's a version compiled for OS X, you could try that.

You might also try posting in the Apple sub-forum; the users there are more likely to be able to help with a Mac-specific problem like this than are the users in this sub-forum.

---

### Post by stoopkitty on 2010-12-25
yay it worked thank you and merry christmas!!

---

### Post by Quackers on 2010-12-25
Aha! Nice result :-)
Thanks srs5694 for the info......again :-)

---

