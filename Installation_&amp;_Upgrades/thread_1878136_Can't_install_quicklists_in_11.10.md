---
title: "Can't install quicklists in 11.10"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by bookcrazy on 2011-11-09
So I tried to install some quicklists for 11.10 and by entering this: 


```
cp /usr/share/applications/nautilus-home.desktop ~/.local/share/applications
```

And I got this:

```
cp: cannot create regular file `/home/++++/.local/share/applications/nautilus-home.desktop': Permission denied 
```

Can someone please tell me what I need to do to fix this?

---

### Post by dino99 on 2011-11-09
sudo may help

---

### Post by bookcrazy on 2011-11-09
> **dino99 said:**
> sudo may help

Thank YOU! Man I feel stupid. I was following the instructions on this site:[http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html]("http://http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html") and their coding didn't have "sudo" before either of the commands they gave.

Once again thanks a million!

---

