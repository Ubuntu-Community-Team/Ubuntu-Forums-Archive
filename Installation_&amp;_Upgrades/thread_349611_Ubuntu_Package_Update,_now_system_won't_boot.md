---
title: "Ubuntu Package Update, now system won't boot"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by fordracerguy on 2007-01-30
Last night there was an ubuntu update. I didn't read what was updated entirely but I believe dbus was. Anyways, now my laptop won't boot. It boots up, detects my mouse and what not, but can't find my hard drive it seems. My system is SATA. I've noticed in the bootup that my cd-rom changed from /dev/sr0 to /dev/hdc. I've tried modifying grub to boot /dev/hda1 instead of /dev/sda1 with the root= option but that doesn't work either. If I let my system sit long enough, it goes to an (initramfs) prompt with an error "/bin/sh: can't access tty; job control turned off". If I scroll up a bit, I do not see any mention of my hard drive. It also says "Unknown parameter 'libata_atapi_enabled' and I get about 20 or 30 unknown symbols relating to ata_scsi, ata_pci, and the like.

Please help me get my system up and running again.

Chris

---

### Post by fordracerguy on 2007-01-30
I just found another error message:

ALERT! /dev/disk/by-uuid/99bb8fd1-2618-487f-a79d-724d4c3c07ad does not exist. Dropping to a shell!

---

