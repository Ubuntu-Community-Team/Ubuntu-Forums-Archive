---
title: "Ubuntu 14.04.2 won't install"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by csiebester on 2015-05-20
The below error occurs when I try to install, it also occurs when I try to check the disk, at least I think it's the same error.  If there are typos I apologize.  Earlier in the day windows stopped booting, I have re installed windows from the CD and it went on.  I ran the memory test on the ubuntu live CD and it passed.  Windows corrected a number of what it said were stranded files as it ran a memory check during it's installation.  The PC is a custom build with a Radeon HD 7950 card, 8 gb of ram, an Asus p8z77-v mb, and i5 processor.  I'm trying to install onto a SSD running windows at the moment though I had planned to just wipe that out.  The computer did take a major hit during my last move I'm afraid so there might be hardware damage.  


[34.922756] ata8.00 exception Emask 0x52 SAct 0x0 Serr 0xffffffff action 0xe frozen
[34.922779] ata8: Serror: {RecovData RecovVomm UnrecovData Persist Proto HostInt PHYRdyChg PHYInt CommWake 10B8B Dispar BadCRC Handshk LinkSeq TrStaTrns UnrecFIS DevExch}
[34.922814] ata8.00: failed command: IDENTIFY PACKET DEVICE
[34.922829] ata8.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 2 pio 512 in
[34.922729]               res 40/00:00:00:00:00/00:00:00:00:00/00Emask 0x56 (ATA bus error)
[34.922863] ata8.00: status: {DRDY}

---

### Post by Vladlenin5000 on 2015-05-20
The problem - if any hardware related - is on the drive you're trying to install. Anyway, the RAM test is fine - I would do it just in case - but not the problem here.

---

