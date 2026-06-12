---
title: "Black screen after I choose Install (using alternative dvd)"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by viru on 2008-05-21
I'm trying to install ubuntu studio 8.04 (so it is a alternative dvd) on my laptop and after it boots, I choose install ubuntu studio and the screen turns black with a "_" flashing, then soon it goes totally black.

The dvd is ok, it works on my desktop and other laptops.

I did tried 7.04 live cd before, and everything worked. however this time the 8.04  (even alternative dvd) does not work.

Is that related to the video driver? (intel x3100)
any solutions? (or i m going to download the 8.04 live cd, maybe it will work)

I did search, didnt find anything related, maybe cause of my poor english :(

Thanks

---

### Post by kellemes on 2008-05-21
Try the following...
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bobblehat on 2008-05-21
The above usually fixes it for sure. If you get stuck, this thread helped me with a similar problem -> [http://ubuntuforums.org/showthread.php?t=756708](http://ubuntuforums.org/showthread.php?t=756708)

---

