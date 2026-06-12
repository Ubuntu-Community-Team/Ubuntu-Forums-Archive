---
title: "Dual Booting (with RAID)"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by Alex W on 2006-10-04
I use Win XP 64 as my primary installation, but have been thinking about Linux for some time - Ubuntu seemed ideal, what with its user friendliness. The CD boot version was astonishing (it even recognised my wireless k/b and mouse!)- I have previously tried to boot into various versions of old windows using CDs, with little success - they won't even install (Ubuntu was quite friendly - a refreshing "hello sir, how may I help?" as opposed to windows traditional kick to the head). But that isn't my gripe.

I got to step 5 of the Install and it asks for partitions. I have set up my 2 HDDs thus - RAID 0'd (with SiI 3114 drivers) and partitioned into PRIMARY [[C: windows]] EXTENDED [[d: games e: apps f: data]] PRIMARY [[I: FAT32 STUFF]] with about 32GB of free space at the end (intended for Ubuntu).

GParted claimed there were 2 separate HDDs with no data on either.

Little help? :-?

---

### Post by _teo_ on 2006-10-04
> **Alex W said:**
> I got to step 5 of the Install and it asks for partitions. I have set up my 2 HDDs thus - RAID 0'd (with SiI 3114 drivers) and partitioned into PRIMARY [[C: windows]] EXTENDED [[d: games e: apps f: data]] PRIMARY [[I: FAT32 STUFF]] with about 32GB of free space at the end (intended for Ubuntu).

GParted claimed there were 2 separate HDDs with no data on either.

Little help? :-?

Personally I've never used RAID, however these links might help:
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://wiki.ubuntu.com/FakeRaidSpec](https://wiki.ubuntu.com/FakeRaidSpec)

---

### Post by Aberrix on 2006-10-04
> **_teo_ said:**
> [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The above link worked for me. In short you need to install a package called 'dmraid' and it will see the RAID array.

---

### Post by Alex W on 2006-10-04
To be honest, I read all of the above and found it hideously complicated - I am totally new to Linux. So I decided on a different plan of action - scrapping the whole RAID system and starting afresh - one hard drive for XP, one for Ubuntu. I suspect Ubuntu will become my OS of choice anyway - XP will be primarily for games.

Thanks anyway.

---

