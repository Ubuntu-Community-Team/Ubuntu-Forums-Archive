---
title: "Tape streamer"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by rpr on 2007-03-30
Hi,

I want to use my tape drive for my backups but I can't get it to work.
It is a BNCHMARK DLT1 SCSI Sequential device. Anyone who can help me out:

cat /proc/scsi/scsi*
```

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: IBM      Model: SERVERAID        Rev: 1.00
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi0 Channel: 00 Id: 15 Lun: 00
  Vendor: IBM      Model: SERVERAID        Rev: 1.00
  Type:   Processor                        ANSI SCSI revision: 02
Host: scsi0 Channel: 01 Id: 03 Lun: 00
  Vendor: BNCHMARK Model: DLT1             Rev: 5E40
  Type:   Sequential-Access                ANSI SCSI revision: 02
Host: scsi0 Channel: 02 Id: 08 Lun: 00
  Vendor: IBM      Model: 39R8711a S320  1 Rev: 1   
  Type:   Processor                        ANSI SCSI revision: 02

```

dmesg | grep scsi
```

[42949402.990000] scsi0 : IBM PCI ServeRAID 7.12.05  Build 761 <ServeRAID 6i>
[42949434.070000] sd 0:0:0:0: Attached scsi disk sda
[42949437.690000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[42949437.690000]  0:0:15:0: Attached scsi generic sg1 type 3
[42949437.690000]  0:1:3:0: Attached scsi generic sg2 type 1
[42949437.690000]  0:2:8:0: Attached scsi generic sg3 type 3
[42949437.900000] st 0:1:3:0: Attached scsi tape st0
```

 sudo mt -f /dev/st0 status
Just hangs

---

### Post by thedtrain on 2007-04-11
Drive: Dell Powervault 100T dat72
SCSI adapter: Tekram DC-390U2WE

I'm having a similar problem:

cat /proc/scsi/scsi*

Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD2500KS-00M Rev: 02.0
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3400620AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI SCSI revision: 05
Host: scsi3 Channel: 00 Id: 06 Lun: 00
  Vendor: SEAGATE  Model: DAT    DAT72-052 Rev: A16E
  Type:   Sequential-Access                ANSI SCSI revision: 03
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3400620AS      Rev: 3.AA
  Type:   Direct-Access  

_______________________________________________

dmesg | grep scsi:

[42949380.500000] scsi0 : sata_promise
[42949380.950000] scsi1 : sata_promise
[42949381.130000] scsi2 : sata_promise
[42949381.180000] sd 0:0:0:0: Attached scsi disk sda
[42949381.200000] sd 1:0:0:0: Attached scsi disk sdb
[42949381.970000] scsi3 : sym-2.2.3
[42949382.180000] scsi4 : sym-2.2.3
[42949382.550000] scsi5 : sata_sil
[42949383.000000] scsi6 : sata_sil
[42949383.000000] scsi: waiting for bus probes to complete ...
[42949389.600000] sd 6:0:0:0: Attached scsi disk sdc
[42949399.970000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[42949399.970000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[42949399.970000]  3:0:6:0: Attached scsi generic sg2 type 1
[42949399.970000] sd 6:0:0:0: Attached scsi generic sg3 type 0
[42949399.980000] st 3:0:6:0: Attached scsi tape st0

_________________________________________________

sudo mt -f /dev/st0 status:

/dev/st0: Device or resource busy

_________________________________________________

I think i may need to enable a module or something but i can't seem to find a correct/straight answer.

Any ideas?  I'll pay!  Anything to get this thing working!

Thanks.

---

### Post by rpr on 2007-04-12
I solved myn.
It was a scsi cable with terminator. A cable without works fine :)
Found it by looking at my working server :)

---

