---
title: "errors in recovery"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by digc16 on 2008-01-29
I just caught these in recovery mode:

[13.852000] BUG: unable to handle kernel NULL pointer dereference at virtual address 0000000
[13.852000] printing eip:
[13.852000] dbfe4540
[13.852000] *pde = 0000000
[13.852000] Oops: 002 [#1]
[13.852000] SMP
[13.852000] Modules linked in: ext3 jbd mbcache sg sr_mod cdrom sd_rom floppy 8139too mii ata_piix ata_generic libata scsi_mod uhcihcd usbcore thermal processor fan fuse apparmor commoncap
[13.852000] BUG: unable to handle kernel paging virtual address 4044e924
[13.852000] printing eip:
[13.852000] c01fde1
[13.852000] *pde = 0000000
[13.852000] Oops: 002 [#2]
[13.852000] SMP
[13.852000] Modules linked in: ext3 jbd mbcache sg sr_mod cdrom sd_rom floppy 8139too mii ata_piix ata_generic libata scsi_mod uhcihcd usbcore thermal processor fan fuse apparmor commoncap


Does this mean Ubuntu hates me?

---

