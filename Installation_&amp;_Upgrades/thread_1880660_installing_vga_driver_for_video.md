---
title: "installing vga driver for video"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by sefarov on 2011-11-14
the graphic of ubuntu 11 kinda chopier.i wana install the windows vga driver.isit possible?help plz.

---

### Post by MAFoElffen on 2011-11-14
> **sefarov said:**
> the graphic of ubuntu 11 kinda chopier.i wana install the windows vga driver.isit possible?help plz.
Be careful what you ask for:
[http://manpages.ubuntu.com/manpages/dapper/man4/vga.4.html](http://manpages.ubuntu.com/manpages/dapper/man4/vga.4.html)

It might be a help if you could post the results of this:
```

lspci -vnn | grep VGA

```Please describe "how" it's choppy. And what driver you are presently using.  If not for your benefit --> Then for mine in helping people with graphics issues...

---

