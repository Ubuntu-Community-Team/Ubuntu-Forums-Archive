---
title: "Dapper Update = dead RAID?"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by najames on 2008-02-06
I have an early 2005 vintage Dapper box with a soft RAID 5.  It uses a a seperate Maxtor 40GB for the OS and 4x160GB SATA II Seagates in the RAID.   The thing has been running fine since I installed Dapper a couple years ago.   I just let it do a massive update, including kernel 2.6.15-51-amd64-k8, and now it is dead, doesn't get to a desktop or prompt stops cold on a  **ata1: translated ATA stat/err**.  I have tried to reboot it a couple times without success.  I started debugging, ran memtest and RAM is ok, I run a live Mint CD and it starts fine, says I have 31GB available, likely the rest of the 40GB Maxtor, so I'm assuming that  the CD, motherboard, and chipset is ok. It seems to leave the RAID as the problem.  

I tried to revert back and run the previous 2.6.15-28-amd64-k8 kernel, but still ran through a millon** ata1: translated ATA stat/err 0x51/40 SCSI** errors.  It has finally gotten to the desktop after about 15 min.  Anyone else have these problems?

I'm gonna try to copy off stuff on this box in case it croaks.

---

### Post by najames on 2008-02-09
Smartctl in Dapper says it can't test Sata drives so I can't test them more now, however after running smartctl on hda and looking at more logs, it looks like the 40GB Maxtor started to puke, seeks failed.  I suspect since this drive has the OS,  it also caused problems on the softRAID. Logs are full of errors like this. Smartctl in Dapper says it can't test Sata drives so I can't test them more now.

ata1: status = 0xd0 {busy}
scsi error return code=0x8000002
sda: Current: Sense Key: aborted Command
Additional sense: Scsi parity error
end request I/O error, dev sda, sector xxxxxxxxxx

2 nights ago it took about 15min to boot.   Last night I tried to reboot this machine at 7:45pm and it was still spewing disk error stuff when I went to bed at 1am, hadn't even reached the logon screen yet.  Taps please.

I doubt if the OS took out the drives, I'd say it is more sheer drive failure.  I'll just stick in a little drive and use it for a scratch testing box, install OS, look at it, wipe it.

---

