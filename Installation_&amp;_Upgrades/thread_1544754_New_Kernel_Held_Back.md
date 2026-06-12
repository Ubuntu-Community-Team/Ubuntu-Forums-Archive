---
title: "New Kernel Held Back"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by gerowen on 2010-08-02
Every time I run an apt-get upgrade command manually to get updates, I see the following in the output:
```

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

```
Anybody know why this is?

---

### Post by Rubi1200 on 2010-08-03
Did you set the system to only apply security updates perhaps?
 
Check (I think it is under this) System > Administration > Software Sources > Updates and see what settings are applied.
 
Hope this helps.

---

### Post by snowpine on 2010-08-03
That is the correct behavior of apt-get upgrade (it never installs new packages). You need to do:

```
sudo apt-get dist-upgrade
```

if you want the new kernel.

---

### Post by gerowen on 2010-08-04
> **snowpine said:**
> That is the correct behavior of apt-get upgrade (it never installs new packages). You need to do:

```
sudo apt-get dist-upgrade
```

if you want the new kernel.

Thank you, this worked.

---

