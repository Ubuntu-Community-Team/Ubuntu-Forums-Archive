---
title: "New drive = GRUB error 15"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by freq on 2006-10-25
I installed Ubuntu 6 on my secondary SATA drive with Windows on my first. GRUB became my primary bootloader; everything worked flawlessly. Then I put in the IDE drive from my old system to get all my documents off it. I plugged it in as master on the first chain, and now I get GRUB error 15 on boot.

Before (working):
sda: Windows XP
sdb1: NTFS media partition
sdb2: Ext2 Linux (Ubuntu)
sdb3: Swap

After (broken):
hda1: Windows XP (old system)

sda: Windows XP
sdb1: NTFS media partition
sdb2: Ext2 Linux (Ubuntu)
sdb3: Swap

Any ideas? I'd like my media. :(

Edit> I also have made sure that the BIOS are setup for SATA1, SATA2, then IDE1 master, so I know it's loading the right bootloader.

---

### Post by Kateikyoushi on 2006-10-25
I think you ran into this "bug" try the recommended solutions. [LINK]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497")

---

### Post by freq on 2006-10-25
Well I'm getting around the issue by using an IDE to USB2 device. It's not exactly what I want, but should provide better flexability. :)

---

### Post by Kateikyoushi on 2006-10-25
Not mentioning less headaches, I made the same decision.

---

