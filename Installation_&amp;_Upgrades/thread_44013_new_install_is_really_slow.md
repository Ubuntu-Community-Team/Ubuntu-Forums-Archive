---
title: "new install is really slow"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by Gwion on 2005-06-24
I`ve installed ubuntu on a pentium III compaq laptop.

It is running so slow, something must be wrong. It takes about a minute for firefox to open up,  and 30 seconds for each new webpage. Open Office takes about 2minutes to open. same goes for everything else. I tried switching to kubuntu, but no luck.

I`m very new to linux, so if you have any terminal commands, please write them in the way/order they would be typed into the terminal.

thanks in advance for your help!

---

### Post by stevenyu on 2005-06-24
sounds like it could be having somethign to do with loopback address missing, do you have a lookbaup address in the name lookup

127.0.0.1

---

### Post by Gwion on 2005-06-24
sorry, don`t know how to do that. could you explain how to do it step by step?

(sorry, I`m a complete linux newbie)

I`m assuming you do it from the terminal?

---

### Post by electrosoccertux on 2005-06-24
I do recall in Redhat I had a similar problem where everything went uber slow...and it did have something to do with either the loopback (127.0.0.1) or something else network related....like I changed my domain name or host name or something and it interfered with my router's assigned domain name.

you done any of this stuff?

The i386 kernel thing sounds like a good idea too. Check the synaptic packet/package manager and maybe do a search for "kernel" or anything else related. Don't know if that'll help; I'm not in ubuntu right now, but thats what I would do if I were.

---

