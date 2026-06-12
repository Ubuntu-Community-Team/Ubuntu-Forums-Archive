---
title: "Backing up the MBR saved my bacon"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by mdebusk on 2007-10-12
I'm posting this in hopes of helping to prevent someone else from screwing up as badly as I did.

Back in August, I was reading about the "dd" command, and the article described how it can back up the Master Boot record. Just messing around, I ran the following command: ```
dd if=/dev/hda bs=446 count=1 > ~/mbr_backup.bin
```

It worked just fine, and I thought, OK, that was neat... and that was it. I forgot about it.

A couple of days ago, I was messing around with LVM under my old install of OS/2 and and I found that it overwrote grub. I searched the forums and tried what I found, but I couldn't manage to get grub back. (I couldn't get it to recognize any of my partitions.) I'd all but resolved to wait for Gutsy and do a full reinstall. But yesterday morning I woke up and remembered having made a backup of my MBR.

As I had a busy day, I waited until a little bit ago, booted from a live CD, mounted my home directory, and ran this: ```
dd if=mbr_backup.bin of=/dev/sda bs=446 count=1
```

I'm once again running Linux. From now on, the first thing I'm doing after setting up a new PC is backing up the MBR.

---

### Post by OoooMatron on 2007-10-12
> **mdebusk said:**
> I'm posting this in hopes of helping to prevent someone else from screwing up as badly as I did.

Back in August, I was reading about the "dd" command, and the article described how it can back up the Master Boot record. Just messing around, I ran the following command: ```
dd if=/dev/hda bs=446 count=1 > ~/mbr_backup.bin
```

It worked just fine, and I thought, OK, that was neat... and that was it. I forgot about it.

A couple of days ago, I was messing around with LVM under my old install of OS/2 and and I found that it overwrote grub. I searched the forums and tried what I found, but I couldn't manage to get grub back. (I couldn't get it to recognize any of my partitions.) I'd all but resolved to wait for Gutsy and do a full reinstall. But yesterday morning I woke up and remembered having made a backup of my MBR.

As I had a busy day, I waited until a little bit ago, booted from a live CD, mounted my home directory, and ran this: ```
dd if=mbr_backup.bin of=/dev/sda bs=446 count=1
```

I'm once again running Linux. From now on, the first thing I'm doing after setting up a new PC is backing up the MBR.


yeah pretty nice, but usually i boot the livecd and install grub and tell it which partition to boot. but nice trick.

---

### Post by mdebusk on 2007-10-12
> **OoooMatron said:**
> usually i boot the livecd and install grub and tell it which partition to boot.

I tried that. Every time, grub gave me an error 21. I couldn't figure out how to get grub to recognize the disks. I could access them from the shell, but grub didn't see them.

I don't know if my partition setup had anything to do with my inability to reinstall grub. I have /boot on sda5, / on sda7, and /home on sda12. I'd have preferred grub to been on sda7 and booting through IBM Boot Manager, but the install DVD wouldn't do that. Now, of course, it doesn't matter to me, as I consider myself to be a Linux user now.

---

