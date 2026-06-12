---
title: "Toshiba NB305: 845G integrated graphics only gives low resolution"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by jondecker76-gmail on 2013-09-09
Hello

I recently helped a friend install Ubuntu 13.04 onto a Toshiba NB305 netbook.  It runs great and everything works, except that it only offers 2 resolutions: 800x600 (4:3) and 1067x600 (16:9).  These resolutions are simply too low and makes using a lot of different software difficult.

I do know that it has an intel 82845G graphics chipset.  I've read that it may be using a generic vesa drive or sorts.  Is there a way I can tell?  Is there a way to force it to use the intel driver?

Any other options would be appreciated.

Thanks

---

### Post by mörgæs on 2013-09-09
Hi, welcome to the fora.

Please run
```
sudo lshw -sanitize > lshw.txt
```

and post lshw.txt in CODE tags.

---

### Post by sudodus on 2013-09-09
The 10.1-inch glossy LED-backlit screen on the Mini NB305-N410 has a 1,024x600-pixel native resolution.

according to this link [http://www.cnet.com/laptops/toshiba-mini-nb305-n410bn/4505-3121_7-33948073.html](http://www.cnet.com/laptops/toshiba-mini-nb305-n410bn/4505-3121_7-33948073.html)

It means that you need an external monitor to get better resolution.

---

### Post by jondecker76-gmail on 2013-09-10
> **sudodus said:**
> The 10.1-inch glossy LED-backlit screen on the Mini NB305-N410 has a 1,024x600-pixel native resolution.

according to this link [http://www.cnet.com/laptops/toshiba-mini-nb305-n410bn/4505-3121_7-33948073.html](http://www.cnet.com/laptops/toshiba-mini-nb305-n410bn/4505-3121_7-33948073.html)

It means that you need an external monitor to get better resolution.

Thanks for the response,  I didn't realize the native resolution was so low.  That surely explains it!

---

### Post by mörgæs on 2013-09-10
Something does not add up: The link provided by Sudodus talks of an Atom with the NM10 chipset, but original post mentions 82845G, which is from the Pentium 4-era. 

As a service to other users who might find the thread please run the command I posted above. It will show without doubt what kind of hardware we are dealing with.

---

