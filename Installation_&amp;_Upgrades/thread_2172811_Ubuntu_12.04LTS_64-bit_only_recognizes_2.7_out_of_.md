---
title: "Ubuntu 12.04LTS 64-bit only recognizes 2.7 out of 6GB of RAM"
date: 2013-09-06
forum: Installation &amp; Upgrades
---

### Post by Peppr on 2013-09-06
Been googling and searching the fora for an hour now, and I can't seem to figure this one out. I've read all about PAE, but that only helps people running the 32-bit version. The output of uname -a is:

```
Linux peppr-desktop-ubuntu 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:01:03 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

So I know I'm running the 64-bit version and PAE shouldn't help. Additionally, free -m gives:

```
             total       used       free     shared    buffers     cached
Mem:          2757       2080        677          0        202        779
-/+ buffers/cache:       1098       1659
Swap:        15999          0      15999
```

I've verified, both in the BIOS and with dmidecode, that there is definitely 6GB recognized by the motherboard. This is a dual-boot machine and Windows 7 (also 64-bit) sees all 6GB. I am using a PCI Express video card with onboard memory, so that shouldn't be the problem either. So there should be no reason why Ubuntu can't use the other ~3.5GB.

I'm hoping that someone in here has some thoughts about what might be wrong. Takers?

---

### Post by sanderj on 2013-09-06
Easy: do this:

```
wget [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py)
sudo python check-my-memory.py
```

It will tell you everything about your RAM. Post the output here.

---

### Post by Peppr on 2013-09-06
Thanks for the note, sanderj! I'll keep that one in my toolbox. FYI I did a bit more digging and realized that there is a newer BIOS version for my motherboard than was installed. Upgrading the BIOS version fixed the problem, although I don't know why. free -m now shows:

```
             total       used       free     shared    buffers     cached
Mem:          5969       1946       4022          0        107        724
-/+ buffers/cache:       1113       4855
Swap:        15999          0      15999

```

which is what I would expect. So we're all set.

---

