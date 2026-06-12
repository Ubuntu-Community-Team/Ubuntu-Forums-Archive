---
title: "qbittorrent doesn't work"
date: 2009-11-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by skeve on 2009-11-26
I tried to run qbittorrent today and there was an error:

```
** (<unknown>:2341): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
qbittorrent: symbol lookup error: qbittorrent: undefined symbol: _ZN9QHashData13detach_helperEPFvPNS_4NodeEPvEPFvS1_Ei

```

And deluge is working strange too, it hangs while quitting.

---

### Post by LKjell on 2009-11-26
some kde apps just fail maybe that is why.

---

### Post by Asraniel on 2009-11-27
i don't think this is a kde app. ktorrent is

---

### Post by skeve on 2009-11-27
> **Asraniel said:**
> i don't think this is a kde app. ktorrent is

...and ktorrent works fine here.

---

### Post by SevenMachines on 2009-11-27
is there a bug open on this? qbittorent just needs a rebuild to fix

---

### Post by SevenMachines on 2009-11-27
[https://bugs.launchpad.net/ubuntu/+source/qbittorrent/+bug/489224](https://bugs.launchpad.net/ubuntu/+source/qbittorrent/+bug/489224)

---

