---
title: "gdesklets broken since last update"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by timosha on 2010-03-23
Since the updates this morning gdesklets is broken. The update displays an error message.

When starting gdesklets in a terminal I get the message "Could not import tiling module!", then it tries to connect to a daemon and then it hangs.

---

### Post by jaoc223 on 2010-03-23
Same for me, I updated an hour ago. Gdesklets broken

---

### Post by timosha on 2010-03-23
I deinstalled gdesklets and installed the previous version out /var/cache/apt en verything works fine again.

---

### Post by Rusna on 2010-03-29
I have this problem still. I tried installing .deb files from /var/cache/apt but without any luck.

---

### Post by timosha on 2010-03-30
Remove gdesklets 0.36.1-4 with synaptic, then install gdesklets 0.36.1-3 out of /var/cache/apt/archives manually.

---

### Post by Rusna on 2010-03-30
The thing is, I only have 0.36.1-4 in apt/archives, and no previous versions.

---

### Post by Rusna on 2010-03-30
Alright, I found from the Internet the 0.36.1-3 deb installer, now it works.
Cheers.

---

### Post by dino99 on 2010-03-30
> **timosha said:**
> I deinstalled gdesklets and installed the previous version out /var/cache/apt en verything works fine again.

need to file a bug

---

### Post by timosha on 2010-03-30
> **dino99 said:**
> need to file a bug

I filed a bug a week ago. But as I am the only user affected it is Canonical tradition that they won't do anything about it.

Amazing is that gdesklets 0.36.1-4 works perfectly in Debian 6.0 Alpha 1 ("Squeeze")

---

### Post by bcroq on 2010-03-31
python 2.5 in Squeeze, python 2.6 in Lucid

[http://packages.debian.org/squeeze/gdesklets](http://packages.debian.org/squeeze/gdesklets)

[http://packages.ubuntu.com/lucid/gdesklets](http://packages.ubuntu.com/lucid/gdesklets)

---

### Post by timosha on 2010-03-31
> **bcroq said:**
> python 2.5 in Squeeze, python 2.6 in Lucid

[http://packages.debian.org/squeeze/gdesklets](http://packages.debian.org/squeeze/gdesklets)

[http://packages.ubuntu.com/lucid/gdesklets](http://packages.ubuntu.com/lucid/gdesklets)

Yep, and the patched gdesklets version 0.36.1-4 for Python 2.6 doesn't work with Python 2.6 in Lucid. The version for Python 2.5, gdesklets 0.36.1-3, works perfectly with Python 2.6 in Lucid.

---

