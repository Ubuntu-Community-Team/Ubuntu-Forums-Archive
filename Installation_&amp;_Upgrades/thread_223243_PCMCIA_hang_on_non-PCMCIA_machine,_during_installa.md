---
title: "PCMCIA hang on non-PCMCIA machine, during installation rather than boot"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by jp.stacey on 2006-07-26
Hi,

I'm trying to install Dapper Drake on a rather elderly PC with no PCMCIA hardware. But however I do it (text/OEM/server, expert mode, various kernel options including hw-detect/start_pcmcia=false, noacpi, nolacpi, pci=no) it invariably gets as far as pcmcia-cs or pcmciatools (?) installation and freezes. There's no PCMCIA in the machine.

It's a seven-year-old 366MHz PII with 128MB memory (hence "alternate" install ISO used) and two hard drives. Dapper Drake is meant to be replacing a Win98 installation on /dev/hda; there's an old Debian installation on /dev/hdb. Its main oddity is an old ne2k ethernet card which has odd IRQ/IO settings, and hence always needs a modprobe.

If this should go elsewhere, apologies and please let me know as I'm new to the Ubuntu community. But I must have wasted around fifteen hours on this problem already just watching blue percentage bars fill with red. 

The difficulty with this freezing is that it happens some two or three hours after beginning the installation, so I'm wasting a lot of time going to the kettle and back...! It also makes it hard to repeat the bug, and as the system freezes I can't see any error messages.

I've read the suggestions here: [https://help.ubuntu.com/community/DapperUpgrades#head-27c927e71a666b3b5064a3c3fa1a3ce31231a8a1](https://help.ubuntu.com/community/DapperUpgrades#head-27c927e71a666b3b5064a3c3fa1a3ce31231a8a1)
but as this happens during installation, and the installation never gets as far as making that partition bootable (or telling LILO it's no longer Win98) then I can't see it being much help, but maybe I'm missing a trick?

Thanks in advance,
J-P

---

### Post by jp.stacey on 2006-07-27
Haven't solved the problem, but I've managed to install breezy badger (5.10) on the system fine.

I hope to move to dapper drake now, but I got as far as dist-upgrade last night when the lightning arrived. Switched off just in time for the power to go out in the whole street!

---

