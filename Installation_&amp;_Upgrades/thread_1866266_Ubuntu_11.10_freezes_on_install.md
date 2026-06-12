---
title: "Ubuntu 11.10 freezes on install"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by PsyclonJohn on 2011-10-21
Hello,

I'm trying to duel boot my system with Ubuntu 10.04 and 11.10, but when I choose to split the hard drive in half, it freezes midway (about 50% in). I've duel booted other computers before with Ubuntu 10.10 and Linux Mint 11 and the partition splitting didn't take long at all.

I've tried twice so far, and it's taking hours...

If anyone knows any information, please let me know!

--
John

---

### Post by PsyclonJohn on 2011-10-24
bump... it's been 2 days.

Anyone know?

---

### Post by richard_wu0313 on 2011-10-24
are you using alternative version?
could you show your dmesg?

alt + F2 
dmesg

i also met the issue, and found some error, but not sure whether the same


ata4: irq_stat 0x00400000, PHY RDY changed
ata4: SError: {Persist PHYRdyChg 1088B}
ata4: hard resetting link
ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata4: configurred for UDMA/133
ata4: EH completed
ata4: Exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozed

---

