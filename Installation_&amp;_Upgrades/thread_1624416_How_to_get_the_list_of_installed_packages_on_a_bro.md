---
title: "How to get the list of installed packages on a broken system?"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2010-11-17
I do have an Ubuntu 10.04 system that does not boot anymore (see [here]("http://ubuntuforums.org/showthread.php?t=1624363")) and if there is no way to fix it, I will have to install it.
For that case I would like to save not only the /home/someuser directory first but also get a list of selected packages that I can use after a fresh installation to automatically install the same packages that were present on the old system.

So, I booted into a Live Ubuntu session ... is there a file or some other way to get the selected packages in a way that is equivalent to: 
```

dpkg --get-selections 

```
Which of course cannot be done on a system that cannot be booted anymore.

---

