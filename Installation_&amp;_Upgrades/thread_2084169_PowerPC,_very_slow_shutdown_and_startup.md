---
title: "PowerPC, very slow shutdown and startup"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by KaiserSose81 on 2012-11-14
Hi all,

I've installed (not without problems) Lubuntu 12.04 on a Powerbook G4 (PowerPC 1GHz, 1 gb ram, Geforce MX 440). Now everything **works perfectly** except the startup and shutdown. To startup my system I have to wait about 3 minutes (and similar time to shutdown)

Giving a look @ /var/log/dmesg I noticed the following

```
[drm] nouveau 0000:00:10.0: Detected an NV10 generation card  (0x017900a5)
checking generic (b8004000 151800) vs hw (b8000000 80000000)
fb: conflicting fb hw usage nouveaufb vs 0Ffb NVDA,Displ - removing generic driver

```

The only issue concerns Nouveau ... inside my /var/log/kern.log says what follows

```
BUG: soft lockup - CPU#0 stuck for 22s!
```

I've booted passing the **"nouveau.modeset=0"**parameter and **the system boot in 15 seconds** but with the famous 'psychedelic' graphics :)

Any idea how to fix the boot/shutdown without getting a 1980 CGA screen? :)

Thanks in advance,
Kaiser

---

