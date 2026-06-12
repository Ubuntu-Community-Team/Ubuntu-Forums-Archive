---
title: "Where put .deb files?"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by goldsby on 2010-08-20
I'm upgrading to Lucid Lynx through the Update Manager.  It timed out a couple of times trying to get the last half-dozen files from the repositories, so I went to the repositories myself through a browser and downloaded the files it wanted "by hand".

To continue through the Update Manager, where do I put the .deb files so that it can find them?

Thanks for any help.

---

### Post by Mr.Comix on 2010-08-21
compeleted
 /var/cache/apt/archives


uncompeleted
 
 /var/cache/apt/archives/partial


beg my bad English
i translated these words from Chinese, i do not know whether it works

---

### Post by goldsby on 2010-08-23
> **Mr.Comix said:**
> compeleted
 /var/cache/apt/archives


uncompeleted
 
 /var/cache/apt/archives/partial


beg my bad English
i translated these words from Chinese, i do not know whether it works

Thanks, that worked.
Your English is no problem.

---

