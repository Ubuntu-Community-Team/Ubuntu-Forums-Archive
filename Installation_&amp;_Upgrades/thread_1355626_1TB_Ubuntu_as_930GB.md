---
title: "1TB Ubuntu as 930GB"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by pluto4ps on 2009-12-15
Hi,
I bought 1TB of HDD to use it with Ubuntu and while installing its shows 930GB is it right?

---

### Post by amauk on 2009-12-15
yes
this is a problem of binary vs decimal notation

When quoting capacity, drive manufacturers will use 10^3 (decimal notation)
meaning 1 Mb = 1000 Kb,
and 1 Gb = 1000 Mb

Binary is obviously 2^10
meaning 1 Mb = 1024 Kb,
and 1 Gb = 1024 Mb

---

### Post by geekman64 on 2010-05-28
hmm...

he is right about that BUT i did the math :)

930GB =**[B] 952 320 megabytes**[/B]
*thats not really 1 TB !*

So this is a FAT32 usb western digital 1TB hard drive? I wonder how much is in use already, eg. system files and what-not?  

32KB one empty folder, created after format. Brand new just out the box..... :popcorn:

Looks like its just bad marketing, or good marketing depending on how you look at it ::):-k

---

### Post by amauk on 2010-05-28
Old thread...!

1 TB
1,000 GB
1,000,000 MB
1,000,000,000 KB
1,000,000,000,000 B
976,562,500 KiB
953,674 MiB
931 GiB
0.91 TiB

---

### Post by srs5694 on 2010-05-28
> **geekman64 said:**
> hmm...

he is right about that BUT i did the math :)

930GB =**[B] 952 320 megabytes**[/B]
*thats not really 1 TB !*

You did *part of* the math. See amauk's response for the complete sequence, which covers more than just the GiB-to-MiB conversion; it goes all the way down to bytes. Better, see [this site](http://physics.nist.gov/cuu/Units/binary.html) (or many others like it) for a description of the whole thing, including the proper suffixes (which amauk uses), some of the history, etc.

---

