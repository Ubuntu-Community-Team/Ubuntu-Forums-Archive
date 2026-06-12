---
title: "Some packages missing in 11.10"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by hopelessone on 2011-12-31
Hi,

I'm trying to install 
> vdr 
vdr-plugin-vnsiserver <- plugin is missing..
vdr-plugin-eepg

Where can i find it? 

Ubuntu 11.10 64bit

Thanks

---

### Post by fdrake on 2011-12-31
any luck with:
```

sudo aptitude search vdr-plugin | grep server

```?

---

### Post by whatthefunk on 2011-12-31
vdr is in the repos. 

```
sudo apt-get install vdr
```

Those two plugins you listed arent.  Try installing vdr and see if it will resolve the plugin issues on its own.

---

### Post by hopelessone on 2012-01-02
Hi,

vdr is in the repos but not the others..

---

