---
title: "md5 mismatch error with feisty to gutsy beta/rc upgrade?"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by master5o1 on 2007-10-12
```
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.bz2 MD5Sum mismatch
```


I am trying to upgrade to the gutsy but this is what I get at the "end" of my Modifying Software Channels part.

---

### Post by waveskiJohn on 2007-10-12
Must be a NZ issue - I have the same problem. How do we get the local repository fixed?

---

### Post by master5o1 on 2007-10-12
We could try to switch to australia because they might be fine. ie. Our nearest.

How might we do that, somewhere we can change it... :P

---

### Post by master5o1 on 2007-10-12
ok, In System > Admin.. > Software Sources set the server to Australia, of Main .. ie.. I'm trying any server closest to NZ that works.

---

### Post by master5o1 on 2007-10-12
taiwan works :D

---

### Post by waveskiJohn on 2007-10-12
I ended up editing the /etc/apt/sources.list and taking the nz. off the front of each of the deb-src files... so I guess I'm getting 50/50 from NZ and US.... seems to be working - probably far from recommended solution though :)

---

### Post by Axed on 2007-10-12
Another NZ'er here having the same problem. I  switched to iinet and it's painfully slow (18k/sec), will try another. 

Geez I feel sad doing this on a Friday night...


edIt: Getting 60k off optus, but it's a far cray from the 500k/sec I'm used to with citylink!

---

### Post by master5o1 on 2007-10-12
damnit... im on Taiwan and getting 30k heh...

why didn't i pursue australia? meh.

edit: getting an occassional 120k hmmm interesting. I suppose that's just a random fluctuation

---

### Post by Axed on 2007-10-12
After starting on 60 it bumped to 100k and then seemed to fluctuate up to 300 for a while (mostly sat around 150k). All up it only took 2 hours, which is pretty good really.

I'm now running Gutsy, and the only issue was the manually installed nvidia drivers which was expected and a 30-second fix. Although "bullet-proof X" didn't seem to do anything.

Pretty impressed so far, aside from the NZ repo issue, this was a smooth upgrade.

---

### Post by waveskiJohn on 2007-10-12
Ditto - about the same time for me...

Similar problem with "bullet-proof X" - this time with an Intel 945 video card (it started but did nothing of consequence)... ah well - I've gotten well versed in sorting out the video settings manually. Not complaining though - desktop effects are stable and lots of other shakey bits fixed.

---

