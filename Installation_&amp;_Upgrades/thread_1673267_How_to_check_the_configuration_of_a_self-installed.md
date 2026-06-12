---
title: "How to check the configuration of a self-installed package?"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2011-01-22
Hi, all:

I'd love to know how to check the original configuration of a self-installed package?
For example, I would like to install the package XXXXX.
I did:

./configure
make
make install


After the installation, I would like to know what the configuration I used for XXXXX's installation. Maybe some dependencies (for example, A,B,C...) were not found so that XXXXX was installed without depending on A,B,C....
However, now, I would like XXXXX depend on A,B,C... 
How to check whether the current installed XXXXX's original configuration?

Thank you very much.

Best Regards
JIA

---

### Post by meson2439 on 2011-01-22
You could probably change some configuration using gconf but most of them would depend on the particular software you wish configure. However, if you wish to know the what dependencies and where is all the installed files were, synaptics will display most of them.

If you build the software yourself using "./configure" and "make install" you could search for the config files inside the same directory where you invoke those command. It's probably something called CONFIG, BUILD or INSTALL. Just edit those files. Its probably written in bash.

I hope it solves your problem.

---

