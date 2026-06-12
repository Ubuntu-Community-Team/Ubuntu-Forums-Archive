---
title: "partitions HELP i screwed up"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by templa edhel on 2007-12-30
ok so im in the middle of the instalation partition menu.NOTE: im using alternate cd and heres how its set u

```
SCSI! (0,0,0,) (sda) - 95.5 gb sts hitachi hts72101 ( this appears to be the total amount of memory
#1 primary 49.3 mb ext2( i meant to make this gb and install ubuntu here)
#2 primary 20gb kntfs (windows is here)
unusable 50.0 gb ( this is what would have  on the ubuntu partiton if it was gb instead of mb
#3 primary 21.5gb ntfs (this is the second hd
unusable 2.0 gb (i partitioned this off of the 21.5 gb partition for swap space(twice my ram size)
#4 primary 5.0gb fat32 (i dont know what this is)
unusable 8.2 mb (i dont know what this is either)
```

so how do i resize the ubuntu partition and how(if i need it) do i get swap space???
plz help i really dont want to loose windows and have to reinstall it.

---

### Post by phidia on 2007-12-30
You need to carefully read the options the installer offers when the partitioning starts. 
The good news is is you didn't click write to disc or make changes (I'm not at an installation menu right now-but the language is something like that) you should be ok. You can exit an install anytime before you actually make changes to your drive and just get back to the state before you ran the cd.
The alternate cd offers you cfdisk as a method of partitioning you probably want to get familar with it _and_ figure out how you want to partition before making the changes to the drive and doing the install.

---

