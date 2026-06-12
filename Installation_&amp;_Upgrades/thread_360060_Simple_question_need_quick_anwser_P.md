---
title: "Simple question need quick anwser :P"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Tuxer on 2007-02-12
Well, my optical drive on my laptop got f*cked up... So no way to put some OS on it... Till I now gut PXE running (netboot)... it seems to work and I got a netboot image from 6.06.

My question is; should I install 6.06 or find some netboot from 6.10?

Like, what are the advantages/disadvantages...


Thanks in advance :)

---

### Post by lhtown on 2007-02-12
6.06 if you value stability and ease of support.
6.10 if you need the cutting edge

For home users, I think Fiesty will be a modest improvement and worthy upgrade for just about everyone.

You can always upgrade to 6.10 from 6.06.

I had a similar problem with a laptop that left me with no way to install the operating system.

I actually bought a US$15-20 adapter on Ebay and took the hard drive out of my notebook, installed it with the adapter into my desktop and installed the operating system. Then I took the disk back out and put it in my laptop and it worked fine. That has been probably a year and a half ago. I don't play on that machine and it has worked fine through two or three upgrades.

Your mileage may vary.

---

### Post by IgnorantGuru on 2007-02-12
You might also try a 1G USB stick ($15).  Depending on your machine it may be able to boot from the USB stick.

You should be able to mount the Ubuntu iso file and copy the files in it to the USB stick.

```
mount -t iso9660 -o loop,ro myexample.iso /mnt/myiso
```

---

