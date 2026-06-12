---
title: "HELP Please"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by TopPretender on 2005-10-09
Hi, i am a newbie using Linux. I want to install ubuntu5.04 on my laptop so i can develop some programs without logging onto shool's workstations. however, i encountered a couple problems:

1) USB flashdrive won't be auto-mount
2) I can't install Anjuta-1.2.4 (make command not found)

so far, these two are the most important issues. I need to solve them asap as my assignment due really soon!!! Thank you everyone!!!!

---

### Post by mlomker on 2005-10-09
> USB flashdrive won't be auto-mount

You'll have to start by seeing if the system is recognizing the drive when it is plugged in:

```

dmesg | tail

```

> 
2) I can't install Anjuta-1.2.4 (make command not found)


```

sudo apt-get install build-essentials 

```

---

### Post by TopPretender on 2005-10-09
here is the info i get from dmesg | tail:

sdb: Write Protect is off
sdb: Mode Sense: 02 00 00 00
sdb: assuming drive cache: write through
SCSI: device sdb: 256000 512-byte hdwr sectors (131 MB)
sdb: Write Protect is off
sdb: Mode Sense: 02 00 00 00
sdb: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi removable disk sdb at scsi3, channel 0, id 0, lun0
usb-storage: device scan compele


So, what next???

---

