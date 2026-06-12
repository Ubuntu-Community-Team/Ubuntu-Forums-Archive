---
title: "Which option to choose when booting from USB on old hardware"
date: 2018-05-04
forum: Installation &amp; Upgrades
---

### Post by prkos on 2018-05-04
These are the options I see in BIOS:

[LIST]
[*]Floppy
[*]LS120
[*]Hard disk
[*]CDROM
[*]ZIP100
[*]USB-FDD
[*]USB-ZIP
[*]USB-CDROM
[*]LEGACY LAN
[*]Disabled
[/LIST]

Hardware: 
AMD Sempron(tm) Processor
2600+
1.61GHz
512 MB RAM

It has old Win XP but I plan to knock that down completely. XP can display this USB contents. 

I made an USB startup disk for lubuntu-18.0-desktop-i386.iso
I tried it on my (newish) desktop and it seems to be working (lubuntu booted), although the system I'm trying to install on is over 10 years old.

---

### Post by C.S.Cameron on 2018-05-04
Can you make the drive first Hard Disk?
That usually works for me.

---

### Post by prkos on 2018-05-04
Thank you for suggesting it, I tried again and I could do that. (When I tried it the first time I must have had the 64bit iso). 

I got this message:

```
Missing parameter in configuration file. Keyword: path 
gfxboot.c32:not a COM32R image 
boot:
``` 

After which I found this:
[https://askubuntu.com/questions/544414/missing-parameter-in-configuration-file-keyword-path](https://askubuntu.com/questions/544414/missing-parameter-in-configuration-file-keyword-path)

And the accepted answer worked! (hit Tab, type live, hit Enter). Live lubuntu is up, now lets see how installation goes :)

Thank you C.S.Cameron!

---

