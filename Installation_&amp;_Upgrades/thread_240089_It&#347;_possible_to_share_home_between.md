---
title: "It&#347; possible to share /home between"
date: 2006-08-20
forum: Installation &amp; Upgrades
---

### Post by cgaviao on 2006-08-20
Hi people, I'm getting my first contact with linux world. I've installed a kurumim (debian based) distribution, and now I'll try Ubuntu.
I would like to know if can I share the sabe /home partition that I've defined on kurumim installation. I dont want to duplicate my personal file like videos, musics, and docs.   Can I?:confused: 

Thanks in advance

Cristiano

Thanks in advance.

---

### Post by ajgreeny on 2006-08-20
In theory you can but be aware that it can cause some configuration problems for different set ups in the different systems, for example, if they both try to use the same config files for different versions of the same program.  Probably worth a try, however, even if it doesn't work for everything.  You can always go back to separate home partitions for each.

---

### Post by noof on 2006-08-20
I'd rather make another partition containing the music, video etc and make a symlink in your home-directory (cd ~; ln -s /usr/mystuff My\ Documents)

---

