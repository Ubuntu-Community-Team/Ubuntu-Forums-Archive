---
title: "Dual Boot win8 + Ubuntu UEFI problem"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by RN_Labs on 2014-03-20
Hello

PC is HP laptop HP250. Upgraded to win 8.1. Shrink main partition. Disabled things in WIN and BIOS as stated in guides about UEFI dual boot.

Started Live USB and installed.

No way Ubuntu starts, no grub menu, only windows 8.

Boot-repair gave me: LOCKED-ESP detected (??)

Boot-repair infos here:

[http://paste.ubuntu.com/7124474](http://paste.ubuntu.com/7124474)

Any idea?

Thank you in advance for help.

---

### Post by RN_Labs on 2014-03-24
Up!

Any help?

---

### Post by oldfred on 2014-03-24
Locked ESP means grub (or anything) cannot write to the fat32 efi partition.

There is a bug report. Sometimes a fsck works, but usual fix is just to fully backup efi partition, delete it, and then recreate it. You can use gparted and be sure to add boot flag as that is what makes it the efi or ESP partition.
Then you can use Boot-Repair to reinstall grub.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)

---

### Post by RN_Labs on 2014-03-25
Thank you very much for your assistance!

Very appreciated!

---

