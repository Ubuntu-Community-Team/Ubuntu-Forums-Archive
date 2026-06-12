---
title: "Stuck at &quot;installing&quot;"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by begone77 on 2006-10-26
I have wanted to switch to Linux for a wile but have never got around to it, well the last few days I figured why not try, so I downloaded and burned Ubuntu, pop-ed it in my dell 4600 and restarted, screen poped up with the install things, I hit "start or install" and a "installing" thing poped up in the top left corner...for the next hour, I have tried a few times, I reburned it to 3 different disks so Im sure its not a bad burn, also my computer is pritty good (1.5 gig of ram, GeForce 6600 GT etc)

so any ideas on this? I searched the forums a few times yet no help

---

### Post by JTux on 2006-10-26
Make sure the ISO image you downloaded is not broken by verifying the file hash.

To do that in windows you need [this]("http://www.beeblebrox.org/hashtab/")

---

### Post by begone77 on 2006-10-26
> **JTux said:**
> Make sure the ISO image you downloaded is not broken by verifying the file hash.

To do that in windows you need [this]("http://www.beeblebrox.org/hashtab/")
I got that app and I got these numbers 

C7CF1B1ACC2BC2E9F285C08EF283502D


C3E3AC2015DAAE2B7235CEA17A45AB019C518F5E



DB53FEE8


that right?

---

### Post by Cynical on 2006-10-26
Compare those numbers to the md5 hash of the iso. You can do this by looking at the md5sums text file. This file is located in the same place as the iso you downloaded. If they don't match exactly, the iso is corrupt and you need to redownload it.

If they do match, please give more detailed information on your problem.

---

### Post by begone77 on 2006-10-26
> **Cynical said:**
> Compare those numbers to the md5 hash of the iso. You can do this by looking at the md5sums text file. This file is located in the same place as the iso you downloaded. If they don't match exactly, the iso is corrupt and you need to redownload it.

If they do match, please give more detailed information on your problem.

I see no md5sums file o_O

---

### Post by Cynical on 2006-10-26
here, find the version you downloaded in this list.

[http://ubuntu-releases.cs.umn.edu//6.06/MD5SUMS](http://ubuntu-releases.cs.umn.edu//6.06/MD5SUMS)

---

### Post by begone77 on 2006-10-26
> **Cynical said:**
> here, find the version you downloaded in this list.

[http://ubuntu-releases.cs.umn.edu//6.06/MD5SUMS](http://ubuntu-releases.cs.umn.edu//6.06/MD5SUMS)

op that did it, it says they do not match, redownloading as we speak

---

### Post by begone77 on 2006-10-26
ah got past that one loading thingie, but now Im getting this error, after it says its trying to mount the thing "timeout waiting for DMA"

---

