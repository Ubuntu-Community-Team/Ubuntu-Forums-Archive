---
title: "Cannot &quot;Apply&quot; Action in Synaptic"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by shadowsai on 2011-04-17
Hello Everyone,
I'm trying to remove my residual configuration packages, however, after selecting them all and clicking "Mark for Complete removal," the apply checkmark remains unclickable. Any help please?

---

### Post by Dutch70 on 2011-04-17
Removed, I misunderstood your post.

---

### Post by Frogs Hair on 2011-04-17
That's very strange , try un-marking the packages then reload synaptic and try again .

---

### Post by shadowsai on 2011-04-19
> **Frogs Hair said:**
> That's very strange , try un-marking the packages then reload synaptic and try again .

I've tried that before, yet it didn't seem to work. Is this an issue with Natty Narwhal? It worked fine in Maverick Meerkat and Lucid Lynx.

---

### Post by mörgæs on 2011-04-19
If you boot the machine, can you run 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge <package-name>
```

?

---

