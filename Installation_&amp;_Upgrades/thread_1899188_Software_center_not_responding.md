---
title: "Software center not responding"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by gameguy on 2011-12-23
I just installed 11.10 onto a laptop I got. It's running in wubi, if that makes a difference. I have not been able to start software center at all. It comes up with a white background when I start it, and the window name is software center. It appears to be responding, but is doing nothing. All the other programs on it work fine, but this one doesn't. I tried uninstalling and reinstalling using apt-get, and also tried
```

sudo apt-get clean all
sudo rm /var/lid/apt/lists/*

```It appears to be responding, however, but I don't know what else to call it. It does nothing. I was letting it start up for 2 hours or so, but it never finished.

The CPU is 5% usage on each of the 1.06GHz cores. The RAM usage is only 600MB / 2GB, so it appears to be running smooth.

It's a celeron dual core netbook running 64 bit, if that helps.

---

### Post by Jack Brown on 2011-12-23
you can try updating it.

sudo apt-get update
sudo apt-get upgrade


or instead of running above commands, which update everything that has an update, you can:
if Update Manager works,  you can select software center updates from there and update them.


or 

you can just try installing Ubuntu on a separate partition.   (after backing up your important files of course), instead of using Wubi which is usually slower.


edit:  for netbooks, you might want to try xubuntu / lubuntu, as the new version of ubuntu uses more video resources.

---

### Post by gameguy on 2011-12-23
> **Jack Brown said:**
> you can try updating it.

sudo apt-get update
sudo apt-get upgrade


or instead of running above commands, which update everything that has an update, you can:
if Update Manager works,  you can select software center updates from there and update them.


I just tried that, and unfortunately, it doesn't seem to produce any results. Upgrade won't make a difference as it is already 11.10. Is there some sort of online listing for programs, cause I can still use apt-get install?


> **Jack Brown said:**
> 
or 

you can just try installing Ubuntu on a separate partition.   (after backing up your important files of course), instead of using Wubi which is usually slower.


edit:  for netbooks, you might want to try xubuntu / lubuntu, as the new version of ubuntu uses more video resources.

I have tried both, and I find that using the normal ubuntu is worth the lack in speed. Unfortunately, I'm not allowed to install it onto a seperate partition.

---

