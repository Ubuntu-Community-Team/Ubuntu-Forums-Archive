---
title: "Where 3GB space got consumed?"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by lalitpratap on 2011-11-25
I have compiled **linux kernel 3.1.2** (latest stable) yesterday on my **Ubuntu 11.10**.
After installation i found that it consumed almost **8GB **more of my hard disk space.
Later when i figure out that the compilation directory(**/usr/src/linux-kernel-3.1.2**) took almost **5GB **of space in source directory. But still unable to figure out where rest **3GB **space get consumed. I am still wondering where this space  get consumed. Anyone having any idea that how can recover that space?

---

### Post by Schugy on 2011-11-25
```
sudo apt-get install gnome-utils
sudo baobab
```
Are you sure that you haven't built a huge debug kernel?
> CONFIG_DEBUG_KERNEL=N

---

