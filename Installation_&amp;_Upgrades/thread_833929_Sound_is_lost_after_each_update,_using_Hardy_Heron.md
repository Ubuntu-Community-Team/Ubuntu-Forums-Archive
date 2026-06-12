---
title: "Sound is lost after each update, using Hardy Heron Upgrade"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by blaise69 on 2008-06-19
Hi there,

I've found a few posts where people have had trouble with some versions of Hardy Heron upgrades, and indeed sound, one solution I found was to install extra modules to fix sound, it's as though the upgrade misses out these modules when it updates it's self.

My problem is that I have to install these missing modules each and every time, it's no longer automatic and I find that unacceptable, I'm not sure why these aren't being picked up, perhaps someone here can help.

Currently if there's a big update recommended by Ubuntu, I'll run it, then restart as suggested, once I'm back to my desktop, the volume icon has become muted, and it appears that sound devices cannot be found. To fix this I have to run the following in the terminal
```
sudo apt-get install linux-ubuntu-modules-2.6.24-19-*
```
Note that 19-* is incremented each time there is an update, I've been doing this since 24-16-*

Once the modules have successfully installed I have to reboot again, upon returning to my desktop for a second time I have sound back.

Is there a way to fix this update procedure?

Cheers,

Blaise

---

### Post by iaculallad on 2008-06-19
Yes, try installing the linux-generic:

```
sudo aptitude install linux-generic
```

---

### Post by blaise69 on 2008-06-19
Ah, I was just reading about that package, in the post the writer also suggested linux-i386 or something as an alternative, should I stick with linux-generic?

---

### Post by iaculallad on 2008-06-19
Linux-generic should be fine. But, try it first if it works for you.

---

