---
title: "cant install any softwares"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by pavankumarl73 on 2010-04-05
recently i installed kubuntu. i tried to install opera,chrome but i got error messages like dependency not satisfiable :libgconf 2-4
i'm new to ubuntu please help

---

### Post by Tylerjd on 2010-04-05
Well first off, Welcome to Ubuntu/Kubutntu!

While I don't specifically use Kubuntu, I can say what it sounds like is that you need to install the dependencies. If you are installing from a .deb pkg file, then this would be true. What you are going to want to do is go to Terminal (**Applications>Accessories>Terminal**) and type the following, ```
sudo apt-get install the-name-of-the-package
```The name of the package being the libgconf. Now before you click enter double tap the TAB button and see if any package name come up. If they do, type in those. If the stuf you have already typed auto-completes, click enter. Give any errors when you do this.

---

### Post by ronnielsen1 on 2010-04-05
How are you trying to install?

---

