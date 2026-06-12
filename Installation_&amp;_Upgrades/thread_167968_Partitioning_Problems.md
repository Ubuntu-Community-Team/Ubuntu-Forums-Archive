---
title: "Partitioning Problems"
date: 2006-04-29
forum: Installation &amp; Upgrades
---

### Post by Harold P on 2006-04-29
Hi,

I'm am trying to install Ubuntu 5.10 Breezy onto this machine. It's totally wiped out (hard drive). When I run the installation and get to the partitioning part, it gives me the following error when I try to set up the tables:

[B]input/output error during read on /dev/ide/host0/bus0/target0/lun0/disc

Retry
Ignore
Cancel[/B]

Why is it giving this error?

Thanks

---

### Post by Kapre on 2006-04-30
[QUOTE=Harold P]Hi,

I'm am trying to install Ubuntu 5.10 Breezy onto this machine. It's totally wiped out (hard drive). When I run the installation and get to the partitioning part, it gives me the following error when I try to set up the tables:

[B]input/output error during read on /dev/ide/host0/bus0/target0/lun0/disc

Retry
Ignore
Cancel[/B]

Why is it giving this error?

Thanks[/QUOTE]

The error is on the hd itself. Check HD as it may have some bad sectors on it already. If HD is OK, check your CD as this maybe causing the problem. Try wiping CD clean or if you d/l it, check the MD5Sum or burn it on a slower speed.

K

---

### Post by Harold P on 2006-04-30
I checked the hard drive itself, scanned it, wrote 0's to it, scanned it again. All seemed fine. Popped in one of the CD's I got from SHIPIT and it gave me the error when I tried partitioning. I guess the disc was just dirty--I'll use a different one.

---

