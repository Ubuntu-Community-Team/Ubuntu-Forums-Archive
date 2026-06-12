---
title: "Can I upgrade in place using the ISO?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by wesg on 2011-10-13
I downloaded 11.10 today and tried to upgrade my 11.04 install inside VMware Player but was turned off by the estimated 8 hour download time, especially after already having a copy of the ISO. 

Is it possible to upgrade in place using the ISO instead of downloading? It seems pointless to use a physical medium to install the software, even if it's only a USB key.

---

### Post by xtjacob on 2011-10-13
You should be able to. Try mounting it with this command:
```
mount -o loop name.iso /mnt/disk
```

---

### Post by 23dornot23d on 2011-10-13
We started discussing this here ..... it may be possible from DVD or Alternate CD
from what I can gather ..... here is the link to the ways we were discussing

[http://ubuntuforums.org/showthread.php?p=11336812#post11336812](http://ubuntuforums.org/showthread.php?p=11336812#post11336812)

---

### Post by wesg on 2011-10-13
Thanks 23dornot23d, I'll be following that discussion with interest... it seems to me this is somewhat of an overlooked feature on the part of the Ubuntu developers. Maybe 12.04...

---

### Post by cabotcat on 2011-10-13
Yes you can. I did this very thing this very morning and am running 64 bit 11.10 right now.

---

