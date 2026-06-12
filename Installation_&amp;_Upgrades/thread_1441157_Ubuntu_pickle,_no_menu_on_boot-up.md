---
title: "Ubuntu pickle, no menu on boot-up"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by WASHAD on 2010-03-28
Ah, when a good deed goes bad. I thought I'd install Ubuntu on my step-dad's computer while I was visiting, because he was having the typical virus problems associated with Windows'

Well, first think, I stopped his Window's from booting up (Ubuntu worked fine). In the process of fixing that, though, I've lost my boot menu so now I can't even run Ubuntu. My trip is about over, now, and I'm facing looks of scepticism while I frantically try to get it going again. 

The last thing I recall was looking at menu.list and noticing that it was empty. I don't think I erased it, but who knows. 

I tried booting from live cd, installing and running grub, and using 'root (hd0); setup(hd0). But that doesn't seem to help. 

I've done a lot of searching but must not be using the right key-words because I can't seem to find a solution. 

I'm becoming a bit desperate and would greatly appreciate any advice. 

Thanks, 

SteveJ

---

### Post by MichaelSammels on 2010-03-28
OK. Hurm. If you still have Windows XP installed, or Windows, try something like this in menu.lst:

```
title Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1
```

However, if you can't even boot into any of your systems you may be looking at a complete reinstall...

---

### Post by WASHAD on 2010-03-28
Thank you kindly for the response;


> However, if you can't even boot into any of your systems you may be looking at a complete reinstall...

Well, I don't have any menu when I boot up, if that is what you mean. Normally, I would expect a menu with options for Ubuntu or Windows. Now, I just get a bash command prompt. It is hard to imagine that I need a complete reinstall, though, simply for having lost my menu (but what do I know). 

With respect to the code:

> title Windows XP
rootnoverify (hd0,5)
makeactive
chainloader +1

Do I use hd0,5 or something else. My partitions are Windows, Ubuntu, and swap. 

Thanks, SteveJ

---

