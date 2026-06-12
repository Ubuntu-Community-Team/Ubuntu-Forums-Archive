---
title: "Update vs Reinstall"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Derek Karpinski on 2011-04-28
I'm running 10.10, and am quite happy with my setup, installed packages, settings, etc.
 
I have my /home folder on a separate partition.
 
I've gathered from the forums here that upgrading can turn into a horror story rather quickly and very often. I'd like to install 11.04 over my 10.10 install but what will I lose?
 
I assume that I will not format my /home when I update, but I'm guessing all installed packages (besides wine that exist in my home folder) will be gone and I'll have to reinstall them.
 
Is there any way to make a list of the packages I have installed now and if I do install 11.04 over 10.10, I could easily automate grabbing those packages?
 
Thanks!

---

### Post by Paulgirardin on 2011-04-28
This will output package information to a file in your home directory.

```
dpkg --get-selections > installed-software
```

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

```
dpkg --set-selections < installed-software
```

followed by

```
dselect
```

---

### Post by xzero1 on 2011-04-28
Didn't know this. Thanks. This info might be good to post in Tutorials and Tips subforum.

---

### Post by Derek Karpinski on 2011-04-28
> **Paulgirardin said:**
> This will output package information to a file in your home directory.
 
```
dpkg --get-selections > installed-software
```
 
And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,
 
```
dpkg --set-selections < installed-software
```
 
followed by
 
```
dselect
```
 
 
Thank you sir! :KS
 
Is there any way to use apt-get instead of dpkg?  From my very limited knowledge of them both, apt-get handles dependencies better.  Or.........I have no idea what I'm talking about. :)

---

