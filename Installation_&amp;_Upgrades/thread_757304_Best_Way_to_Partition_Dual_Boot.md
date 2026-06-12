---
title: "Best Way to Partition Dual Boot?"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by seismicmike on 2008-04-16
My current laptop is a piece of crap. It's really old and it shorts out and stuff, so I need to get a new one. I went back and forth for a while about whether to get a [Dubuntu]("http://www.dell.com/content/topics/segtopic.aspx/ubuntu?c=us&cs=19&l=en&s=dhs&dgc=IR&cid=11973&lid=471885") (Dell + Ubuntu) and also looked at [gbook]("http://www.everex.com/products/gbook/gbook.htm"), but ultimately decided that since I'm going to be using it primarily for web design it wouldn't hurt to have windows for test purposes...

So I'm going to probably buy a Dell with Windows Vista and dual boot Ubuntu 8.04 (since I'll probably buy in June), but I was wondering if you, the crowd at large, have any opinions on the best way to go about partitioning it? I would obviously like to have it set up so that I can access all of my files from both Operating Systems, so from where I sit it looks like the best idea is to give Linux the minimum space it needs to operate (what do you think.... 10gb?) and have the rest go on the Windows partition (since ntfs-3g is so awesome!)

So the question I really have is, does anyone do this? Do they have any ideas/suggestions.

Is there any way to configure my linux install so that my "My Documents" folder in Vista is used by Ubuntu as my home folder?

Diolch yn fawr

---

### Post by Pumalite on 2008-04-16
The best guide around:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by seismicmike on 2008-04-16
Thanks. I'm looking it over and it looks good so far, but I had another thought. What about Wubi? Would I be able to access my Windows files from Ubuntu on a Wubi install?

---

### Post by oilchangeguy on 2008-04-16
> **seismicmike said:**
> Thanks. I'm looking it over and it looks good so far, but I had another thought. What about Wubi? Would I be able to access my Windows files from Ubuntu on a Wubi install?

your best bet is to stay away from any type of vm program. and do a proper dual boot. that way both os's will have full use of the computers resources. also with all of the problems Microsoft is having with Vista. i'd suggest buying a computer with no os. and buy a copy of XP Pro (xp will still be avail. til june) and install it. then ubuntu.

---

### Post by Pumalite on 2008-04-16
Or get rid of Windows all together and later run it in Virtualbox if you want to play some games.

---

