---
title: "Why won't xserver-xorg-input-wacom install?"
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ubuntiac on 2010-01-22
When I try to install it with apt-get I get told:
```
The following packages have unmet dependencies:
  xserver-xorg-input-wacom: Depends: xserver-xorg-core (>= 2:1.6.2)
```

As far as I can see that means it needs xserver-xorg-core version 1.6.2 **or higher**.

apt-cache show xserver-xorg-core says:
```
Package: xserver-xorg-core
[...]
Architecture: amd64
Source: xorg-server
Version: 2:1.7.3.902-1ubuntu9

```

So doesn't this mean I have version 1.7.3, but it's complaining I need 1.6.2 **or higher**?

I'm confused! :confused:

---

### Post by tepsipakki on 2010-01-22
But it also conflicts with drivers that provide the old ABI, so it refuses to install. The old driver was also removed from the archive and a new one accepted just now, so you'll be able to install it before too long. Works at least with my Intuos4.

---

### Post by Ubuntiac on 2010-01-22
Ah, ok. So it had nothing to do with the version number. Thanks for clearing that up! Do you mind me asking where I'd find "Incoming" mentioned here?:

> This may mean that you have requested an impossible situation or if you are using the unstable distribution 
that some required packages have **not yet been created or been moved out of Incoming.**

Is it publicly visible?

---

### Post by naught101 on 2010-02-13
This seems to be fixed for me now.. xserver-xorg-input-wacom installs fine.

---

### Post by Favux on 2010-02-13
Hi naught101,

If you look at the package number you'll see that's because it's really Xorg's xf86-input-wacom-0.10.3.

---

