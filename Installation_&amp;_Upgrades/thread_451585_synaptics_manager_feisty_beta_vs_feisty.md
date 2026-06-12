---
title: "synaptics manager feisty beta vs feisty"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by analyzer123 on 2007-05-22
Hi,
     I had originally installed the feisty beta version of Ubuntu. I recently got the CD of Feisty release  and deleted my original beta install CD. Now when I try to install some new package and if it needs files from the CD, synaptics complains saying I must install the CD labeled "XXXX Fesity_beta_xxxx". It refuses to read from the final feisty release CD. How do I fix this problem?

Thanks.

---

### Post by xodeus on 2007-05-22
Look in your /etc/apt/sources.list
Change the line containg the cd to:
```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

```
Then update apt

---

### Post by zvacet on 2007-05-22
Or just comment that line and you will not be asked for CD.

---

