---
title: "/dev/sda* insted of /dev/hda*"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by constchar* on 2008-01-24
Anyone having issues with Ubuntu 7.10 recognizing IDE drives as SATA drives?
I'm installing Ubuntu 7.10 Server Edition on an older Pentium 3 PC with a 440BX Intel motherboard
and my hard drives show as SATA drives but apparently it seems to read and write the drives
just fine despite.

---

### Post by Rhubarb on 2008-01-24
Yes, I can't remember where I read it, but ubuntu refers to sda only now.
Everything still works, just a name change :)

---

### Post by wieman01 on 2008-01-24
Same here. Nothing we ought to worry about I guess.

---

### Post by dgray_from_dc on 2008-01-24
sda, b, c, etc. doesn't actually stand for SATA it's SCSI.  For a long time, anything non-IDE is channeled into the SCSI interface, USB, Firewire, etc.  I think that the hd to sd change occurred in Edgy or Feisty.  Dapper still uses hd.  It may have something to do with handling all drives as if they're SCSI.  It may make it easier for software development or something.  Kinda sucks for me, on my server, I boot from IDE and have a USB-based RAID 5.  It was more convenient to have the RAID in an entirely different group of identifiers.  Still works though.

---

### Post by electronpusher on 2008-02-19
> **wieman01 said:**
> Same here. Nothing we ought to worry about I guess.

I'm sure you're right but I'm still curious. I'm using Dapper but experimenting with Gutsy on an old computer. What do you think would happen if I actually did have a SCSI device? Does anyone know what advantage there is to doing it like this? When I partitioned the drive and I saw sda instead of hda I thought something was really wrong. Does anyone know where we can find out more on this? Thanks!

---

