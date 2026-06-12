---
title: "Trouble after install of 64 bit Dapper.  Kernel Panic"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by dahli.llama on 2006-06-29
Ok, I tried the graphical upgrader last night, since I've never tried that route, and today when I tested my system, it would boot up, but never make it into X (I assume because the nVidia graphics drivers weren't loaded yet) and then when I went to load the drivers I got a kernel panic error.  It did this every time, so I assumed I have mucked something up, and decided to do a clean install.

Today, I loaded up the 6.06 64-bit desktop disk that I downloaded and burned and went to work (actually I'm typing this using the Live CD environment).  Everything installed fine (although it did have some trouble booting up when I had my second monitor attached *shrug*), and I went to reboot.  Grub had misdetected my root partition, so I needed to edit that, but then everything seemed to boot fine until I got into it.  Everything loaded and I was able to see the desktop.  I immediately hit Alt-F1 and went into a virtual terminal to check things out when the computer crashed again.

These are the errors I got:
```

[161.374723] hdc:timeout waiting for DMA
[164.058655] 
[164.058656] CPU0: Machine check exception  4bank4:b200000000070f0f
[164.075155] TSC 4c8b968dfe
[164.080902] kernel panic - not syncing: machine check
[164.086745]

```

My pc specs:
AMD Athlon64 3200+
ASRock 939Dual SATA2 motherboard
1Gb DDR400 RAM (dual channel)
Nvidia GeForce 6600 GT
Sound Blaster Live! Value
80Gb SATA hard drive (this is the primary with Ubuntu installed on it)
200Gb IDE hard drive (this is for backups and suck.  It was not formatted during the install)

I had Ubuntu 5.10 64-bit installed prior to this and everything was working perfectly.

Could anyone give me any suggestions on what to do?

Thanks!

---

