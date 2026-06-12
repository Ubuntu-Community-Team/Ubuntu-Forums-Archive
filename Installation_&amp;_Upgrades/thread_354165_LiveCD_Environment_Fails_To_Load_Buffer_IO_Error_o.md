---
title: "LiveCD Environment Fails To Load: Buffer I/O Error on device sr0"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2007-02-05
Hello,

I used Ubuntu 6.06 LTS once before, but switched to Gentoo. I have decided to switch back to Ubuntu and downloaded the ISO for 6.10. The ISO burn went smoothly, but when loading I get this error:

```
[17179709.648000]Buffer I/O error on device sr0, logical block 357566.
```

I am assuming that sr0 would be the hard drive, which is a SATA 100 GB (20 GB allocated for Linux partitions). If anyone could help, that would be great.

Thanks,
Dylan Nugent
Director of Product Development
Tranzerk Technologies
[email]dnugent@tranzerk.com[/email]

---

### Post by Dylnuge on 2007-02-05
Please help. I need to get Ubuntu up and running by tomorrow. I have a presentation/demo of it (we are switching all the workstations over, and I need to present it so people know what is happening).

Thanks,
Dylan Nugent

---

### Post by Dylnuge on 2007-02-05
Note that I tried booting in Graphics Safe Mode, same error. BTW: The Number after the decimal changes (648000, 900000, and more), but the block number and first numbers (357566 and 17179709) do not.

---

### Post by Dylnuge on 2007-02-05
Somebody please help! Sorry for bumping, but I need to get this resolved ASAP.

---

### Post by Dylnuge on 2007-02-05
It works with 6.06 LTS. I am still having the follwing two problems:

1. Need to fix clock (when I use Ubuntu it wants GMT then calculates, switching windows to GMT, when I use windows it syncs, switches it back, and causes Ubuntu to display the wrong time. I need to make one of them comply with the others time format (set Ubuntu to local, ot Win to GMT-6) so that I can use them effeciantly).

2. Need to get wireless running. Then I can update and all that. It used to work out of the box, but I upgraded pc to a newer device using Intel ipw3945. If I can get some help with installation and setup, that would be greatly appreciated.

Thanks,
Dylan

---

### Post by hitu on 2008-02-18
I have the exact same problem, but only in a Virtualized Environment (tried Virtual Server 2005 R2 SP1 & Virtual PC 2007, haven't tried VMWare yet).
I used the same .ISO and burned a CD of it and it installed perfectly on my Dell XPS 420.
Wonder whats wrong, didn't find any relevant searches on Google :(
Downloading VMWare rigt now, wel let know of what happens.

---

