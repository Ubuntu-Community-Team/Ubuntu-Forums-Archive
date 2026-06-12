---
title: "can't boot livedvd with sata hdd plugged in"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by drenzu on 2006-06-22
Hi there

I downloaded and burned the livedvd image for kubuntu dapper. It boots fine on my laptop, but not on my desktop.

The problem occurs after "starting evms". The screen goes black, then prints something like this:
```
ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
ata1: translated ATA stat/err 0x51/40 to SCSI SK/ASC/ASCQ 0x3/11/04
(etc..)
IRQ 217: nobody cared.
```

And then more of the same.

I tried unplugging my sata harddrive, and without it plugged in the problem does not occur. Unfortunately, without the harddrive plugged in, I can't install ubuntu :roll: 

Is there a way of turning off EVMS at the boot menu? Or some other workaround? Has anyone else had the same problem?

---

### Post by drenzu on 2006-08-13
*bump*

No-one has any ideas? What about the alternate install disk - does anyone know if EVMS can be disabled when booting from that?

---

### Post by drenzu on 2006-08-16
Found a solution. Simply pressing Ctrl+C when EVMS was loading worked for me.

---

### Post by osarusan on 2006-09-24
Is this a good solution?? Is EVMS required or better to have enabled?

I'm having the same problem, so I want to know what the best solution is, rather than just disabling it like this every single time I boot.

---

### Post by chadlongstaff on 2006-10-20
Hi I've been having identical issues with one of the machines I look after, as far as I can tell from my googling the issue is a bad controller. This link may prove useful: [http://www.romantika.name/v2/category/computing/linux/](http://www.romantika.name/v2/category/computing/linux/)
under the heading "Storage Emergency"

---

