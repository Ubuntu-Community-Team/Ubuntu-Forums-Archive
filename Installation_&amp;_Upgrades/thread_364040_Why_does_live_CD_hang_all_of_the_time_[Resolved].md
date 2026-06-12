---
title: "Why does live CD hang all of the time? [Resolved]"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by t341 on 2007-02-17
I misspelled "hang" in the header

I have been trying the Edgy live cd before I upgrade from dapper
and I notice that It hangs most of the time I try to boot up and it
only runs properly one out of every 10 attempts.
Does anyone else have this problem with notebook computers
and will any of the boot options at the bottom of the screen help 
any?

---

### Post by bmk789 on 2007-02-17
you can try booting with noacpi

this helps some people

---

### Post by aysiu on 2007-02-17
Maybe you don't have enough RAM?

---

### Post by t341 on 2007-02-18
Thanks  I tried noapic and it worked this time

I could use some more ram, but this laptop
computer is hard for me to upgrade the memory
with.

---

### Post by aysiu on 2007-02-18
How much RAM *do* you have? 128 MB? 256 MB?

---

### Post by t341 on 2007-02-18
512 mb

---

### Post by aysiu on 2007-02-18
That's plenty of RAM. Could it be something wrong with the CD itself? Did you [do a checksum on the ISO](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_check_MD5_checksum_of_files) to make sure it didn't get corrupted during download? Did you burn it at a slow speed?

---

### Post by t341 on 2007-02-18
> **aysiu said:**
> That's plenty of RAM. Could it be something wrong with the CD itself? Did you [do a checksum on the ISO](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_check_MD5_checksum_of_files) to make sure it didn't get corrupted during download? Did you burn it at a slow speed?

I burned it with infrarecorder and used the default record speed.
Anyway, I got it to work with the boot command 'noapic'

---

