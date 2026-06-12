---
title: "[SOLVED] Partition Help for new install"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by baserunner_ams on 2008-09-28
Hello all,

thanks for the help :)
I have searched the forums and googled the web without finding a conclusive anwser. Thats why i post here now.

My Hardware:
- CPU: Intel Core 2 Quad Q6600
- RAM: 4GB (inted to extend that to 8GB in the near future)
- HDs: 3 * 500GB SATA
- MoBo: Asus P5Q Pro

My Goal:
Setup Ubuntu 64bit (no 4GB AM limit) and use the FakeRAID 5 of the motherboard
(i found this links very helpful for that purpose: 
[http://hol.net.nz/blog/kubuntu-with-fakeraid]("http://hol.net.nz/blog/kubuntu-with-fakeraid")
[https://help.ubuntu.com/community/FakeRaidHowto?]("https://help.ubuntu.com/community/FakeRaidHowto?")
)

I want to run a couple of virtual servers on this hardware (XP, Vista, my production webserver development copy,...)

From my research so far i ound that i need:
- /SWAP ~8GB
- /boot ~2GB
- / (root) ~20GB
- /home rest

what about other partitions i found like:
/var
/etc
/usr
/tmp
...

any help will be appretiated

---

### Post by Vivaldi Gloria on 2008-09-28
I don't know about FakeRAID but let me comment on your partitioning:

> **baserunner_ams said:**
> 
From my research so far i ound that i need:
- /SWAP ~8GB
- /boot ~2GB
- / (root) ~20GB
- /home rest


For boot 150MB is enough. If you're going to compile your own kernels then increase it to 500MB.

8GB Swap is huge. I also have a Q6600 with 4GB ram. I don't use more than 200MB swap in general use. I'm yet to see anything over 450MB.

20GB root is OK. You can reduce it to 15GB.

> what about other partitions i found like:

In a desktop system these partitions are not necessary in general. Don't bother making them.

---

### Post by baserunner_ams on 2008-09-28
Thanks for the answer.

---

