---
title: "After Minimal Install And MATE The Screen Is Stuck At 1024x768"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by user2037 on 2013-02-06
Apparently the video card is not being handled properly. It is a Compaq 6710b with Intel GM965.

---

### Post by tgalati4 on 2013-02-08
I had a successful install of Linux Mint 14 Mate 64-bit on an Acer Extensa 4620Z with a GM965 graphics card.  It displays full resolution, but will not resume properly.

I would do a fresh install instead of minimal install then adding MATE, since that may introduce other system errors.

In the meantime, look through /var/log/Xorg.log.0 for errors.

---

### Post by MAFoElffen on 2013-02-09
> **tgalati4 said:**
> I had a successful install of Linux Mint 14 Mate 64-bit on an Acer Extensa 4620Z with a GM965 graphics card.  It displays full resolution, but will not resume properly.

I would do a fresh install instead of minimal install then adding MATE, since that may introduce other system errors.

In the meantime, look through /var/log/Xorg.log.0 for errors.

Actually, please attach your /var/log/Xorg.0.log as a text file...
```

cp /var/log/Xorg.0.log ~/Documents/Xorg.0.log.txt

```

Then 
```

sudo apt-get install hwinfo
sudo hwinfo --framebuffer > ~/Documents/framebuffer.txt

```
and attach framebuffer.txt

---

