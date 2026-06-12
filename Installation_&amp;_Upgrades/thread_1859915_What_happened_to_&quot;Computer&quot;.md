---
title: "What happened to &quot;Computer&quot; ?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by EmporerD on 2011-10-14
I just upgraded to 11.10 and all is well except that it doesn't seem to have Ubuntu's equivalent to a My Computer application. I have multiple partitions on my computer and it made accessing them really easy and convenient. Does anyone know how I can get it back?

---

### Post by sikander3786 on 2011-10-14
For enabling it, go to a Terminal and run:

```
sudo apt-get install dconf-tools
```

Press Alt + F2 and enter:

```
dconf-editor
```

Navigate to "org > gnome > nautilus > desktop" and enable "computer-icon-visible".

---

### Post by EmporerD on 2011-10-14
That worked, thanks. :p

---

### Post by collisionystm on 2011-10-14
gnome-tweak also sets these changes in unity.

---

### Post by sikander3786 on 2011-10-14
Well, Yeah.

I just recently wrote a post on that and forgot immediately :D

[http://www.tuxgarage.com/2011/10/gnome-tweak-tool-and-ubuntu-oneiric.html](http://www.tuxgarage.com/2011/10/gnome-tweak-tool-and-ubuntu-oneiric.html)

---

