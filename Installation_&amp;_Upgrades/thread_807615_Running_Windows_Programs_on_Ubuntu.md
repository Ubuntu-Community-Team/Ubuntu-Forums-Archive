---
title: "Running Windows Programs on Ubuntu"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by andrecamp on 2008-05-26
How do I run windows programs on Ubuntu?
I need to run programs such as Dreamweaver
and Photoshop CS2.

I heard of this but I never found anything about Ubuntu on the site.

[www.winehg.org](www.winehg.org)

---

### Post by Bakon Jarser on 2008-05-26
> **andrecamp said:**
> How do I run windows programs on Ubuntu?
I need to run programs such as Dreamweaver
and Photoshop CS2.

I heard of this but I never found anything about Ubuntu on the site.

[www.winehg.org](www.winehg.org)

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

photoshop cs1 and cs2 will work.  looks like dreamweaver version 8 works well.

---

### Post by andrecamp on 2008-05-27
One problem with Photoshop. Photoshop says it is unable to find the fonts. :S

---

### Post by Bakon Jarser on 2008-05-27
See if this helps.  Go to the terminal (Applications > Accessories > Terminal) and type

```
sudo apt-get install msttcorefonts
```

---

