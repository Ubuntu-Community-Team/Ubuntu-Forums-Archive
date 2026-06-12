---
title: "Error when running from USB flash drive - BusyBox"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by itsjareds on 2008-09-20
I followed instructions from [this site]("http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/") on how to run Ubuntu from a flash drive on any computer. I did everything right and booted it up, and it booted perfectly the first time. However, ever since that first time I can't get it to load again.

I've gotten this BusyBox many times.. I hate that word. This is what it says right before the BusyBox comes up:

```

sd 6:0:0:0: [sdc] Attached SCSI removable disk
sd 6:0:0:0: Attachd scsi generic sg4 type 0
sr2: scsi3-mmc drive: 48x/48x tray
sr 6:0:0:1: Attached scsi generic sg5 type 5
end_request: I/O error, dev fd0, sector 0
Registering unionfs 1.4
unionfs: debugging not enabled
loop: module loaded
squashfs: version 3.3 (2007/10/31) Phillip Lougher
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0

```

I don't know what this means.. except that there was an input/output error. My flash drive's ID is sdb, so I'm not sure if it's the same thing. I've tried it on two computers now. I also booted with the all_generic_idle option and removed quiet splash. 

Does anybody have tips?

---

### Post by Pumalite on 2008-09-20
Your link is dead.

---

### Post by itsjareds on 2008-09-20
Oh sorry, the URL function added an extra http://

It's fixed now.

---

### Post by Pumalite on 2008-09-20
I'd recommend this other method to you:
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)

---

### Post by itsjareds on 2008-09-20
Thanks, that's what got it working. Now it works just like my installation on my hard drive.

---

