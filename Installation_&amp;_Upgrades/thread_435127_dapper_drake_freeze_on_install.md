---
title: "dapper drake freeze on install"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by buzzbo on 2007-05-06
Trying to install dapper drake (6.06 LTS), and it is freezing up at or about this spot:

```
* Preparing restricted drive [OK]
* Starting basic networking [OK]
* Starting kernel event manager [OK]
* Loading hardware driver
* Starting PCMCIA services
* PCMCIA Not Present
* Loading manual driver
```

no further progress after this point.  I tried the first two options to install (standard & graphical/safe).   I am running this on a new HP pavilion dv9000 notebook with the following specs:

AMD turion 64 x2
1 GB RAM
120GB SATA with the following partitions:
[I]/dev/sda1 NTFS ~85 GB
/dev/sda2 ext3 ~20GB
/dev/sda3 extended
/dev/sda4 linux swap 2GB
/dev/sda5 FAT32 10GB[/I]

---

### Post by TristanPhillips on 2007-05-08
Have you tried booting with the "noacip" option?

---

### Post by buzzbo on 2007-05-08
do you mean noapic? read on... :)

I visited the #ubuntu IRC channel and someone suggested the alternative desktop, or fiesty.  A had similar problems with both.  Then, I recalled "noapic" and this successfully booted with the fiesty livecd.  

After reinstallation, I had similar boot issues, and so I added "noapic" to the boot line in menu.lst for the grub installer.

So I am booting OK, but I wonder if "noapic" should be considered a temporary thing and I should be looking for a long-term solution to what appears to be a hardware issue?

Buzz

---

