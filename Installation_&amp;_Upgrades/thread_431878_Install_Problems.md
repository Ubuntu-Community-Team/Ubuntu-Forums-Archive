---
title: "Install Problems"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by Khashul on 2007-05-03
I'm having some problems with a new Ubuntu 7.04 install on our media computer.

First of I'd like to state that this is me doing it for my Dad while he is away and I have very little Linux experience other than using it for a year or so lightly.

On our machine we had a system set up that runs all our media and holds movies/music etc. On the PC are 2 hard drives, A 40Gb one and a 300Gb drive. The smaller one is used for the system files and the large one used for movies.

On Fedora we had it set up to be:

40Gb = HD1 = / = System
300Gb = HD0 = /Samba = Movies etc

I'm now using the LiveCD to set up the partitions but I'm getting an error while doing it. The error I receive is "Cant have the end before the start!"

I have no idea whats causing this and cant seem to work around it at all. 

I hope I've been able to give you the necessary information because I am quite lost with all this at the moment.

---

### Post by rillip on 2007-05-03
Can you describe the partitioning  a little more?  When exactly are you getting the error?

---

### Post by Khashul on 2007-05-03
Well I set up the 40Gb drive as an ext3 and a swap drive as /, its primary and position is set to start.

When i try to set up the second drive as /samba and with either Start or End, all types of formatting types i still receive the error.

---

### Post by jpatton on 2007-05-03
I don't know what other's might say, but since the 300gb drive has all the stuff you want to keep, I might suggest unplugging it just in case, ya know? Then just run the install and tell Ubuntu to setup the drive for you, after it installs, then plug the big drive back in, modify fstab to include the new disk and mount it to /samba.

Certainly not the only way, perhaps not even the best way, but quite possibly the safest way :)

Good luck

---

### Post by Khashul on 2007-05-03
I dont mind about the 300Gb drive, we have a backup of that so I dont mind formatting, its just that i cant :(

---

