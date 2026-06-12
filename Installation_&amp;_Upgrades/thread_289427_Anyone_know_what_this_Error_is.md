---
title: "Anyone know what this Error is?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-10-30
Hey folks!
Anyone know what this Error is and how I can correct it?
Thanks!

---

### Post by blind0wl on 2006-10-30
Looks like emacs21 is broken and the dependancy's that rely on it cannot be installed because of it.

If I was you, I'd do a 

```
sudo apt-get remove emacs21
```

and re-install it

```
sudo apt-get install emacs21
```

Then try installing whatever you were doing in synaptic

Cheers

Blindy

---

### Post by randell6564 on 2006-10-31
> **blind0wl said:**
> Looks like emacs21 is broken and the dependancy's that rely on it cannot be installed because of it.

If I was you, I'd do a 

```
sudo apt-get remove emacs21
```

and re-install it

```
sudo apt-get install emacs21
```

Then try installing whatever you were doing in synaptic

Cheers

Blindy
Thanks My Friend! I'm on it!  Let ya know what happens!

---

### Post by randell6564 on 2006-10-31
It worked 'blindOwl', Thank You!
Dont know what this was about, but it worked.,so what the Fu%$!:-D

---

### Post by blind0wl on 2006-10-31
Sometimes the apt repositories get a bit funny...nothing to worry about in the long term.

Glad your problem is fixed.

Cheers

Blindy

---

