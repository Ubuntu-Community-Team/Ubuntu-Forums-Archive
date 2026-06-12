---
title: "ubuntu isreally really slow"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by Gwion on 2005-06-24
I`ve installed ubuntu on a pentium III compaq laptop.

It is running so slow, something must be wrong. It takes about a minute for firefox to open up,  and 30 seconds for each new webpage. Open Office takes about 2minutes to open. same goes for everything else. I tried switching to kubuntu, but no luck.

I`m very new to linux, so if you have any terminal commands, please write them in the way/order they would be typed into the terminal.

thanks in advance for your help!

---

### Post by manicka on 2005-06-24
[QUOTE=Gwion]I`ve installed ubuntu on a pentium III compaq laptop.

It is running so slow, something must be wrong. It takes about a minute for firefox to open up,  and 30 seconds for each new webpage. Open Office takes about 2minutes to open. same goes for everything else. I tried switching to kubuntu, but no luck.

I`m very new to linux, so if you have any terminal commands, please write them in the way/order they would be typed into the terminal.

thanks in advance for your help![/QUOTE]
 how much ram do you have?

---

### Post by Gwion on 2005-06-24
over 300 ram. can`t remember the exact number. it had windows 2000 running on it before, and it wasn`t even close to the slowness of ubuntu on it.

---

### Post by tread on 2005-06-24
It might be a DMA issue, check settings using hdparm.
I'm no hdparm expert though,  so you'll have to google for info.

---

### Post by Ken.Lank on 2005-06-24
[QUOTE=Gwion]over 300 ram. can`t remember the exact number. it had windows 2000 running on it before, and it wasn`t even close to the slowness of ubuntu on it.[/QUOTE]
 My guess is you need to change from the i386 kernel to the i686 kernel.  I'm very new at this too and a co-worker changed mine and it seems to run much faster.  I believe it was done through "Synaptic Package Manager", but I'm not sure if he did anything else.  Sorry I can't help more, but I'm in the same boat.

---

