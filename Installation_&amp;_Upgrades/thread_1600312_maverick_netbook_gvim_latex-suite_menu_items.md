---
title: "maverick netbook gvim latex-suite menu items"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by atozer on 2010-10-18
On eee1000 I have installed gvim with latex-suite and run;
            vim-addons -w install latex-suite  .

With tex file open latex-suite keyboard shortcuts work e.g. SSE, SPG, ==, `b, F5, F9, \ll, \lv.  However the latex-suite menu items do not appear in the menu bar.

Has anyone else had to overcome this?

---

### Post by hasana on 2010-12-29
Hello,
I am seeing this problem too with latex support for gvim on my netbook. The same (at least as far as I can tell) installation works fine on my laptop. Does anyone have any ideas?

Hope that the New year will be a good one for you,
adil

---

### Post by Resting_stage on 2011-04-27
Same here. Latex-suite works fine on a desktop with Xubuntu 10.04, but menu items only appear on UNB 10.10 when I sudo gvim

---

### Post by Resting_stage on 2011-04-28
An addition to my previous posting: the problem seems related with Unity in Ubuntu NBR. When I run latex-suite in an Openbox session on the same computer, the latex menu entries are there in gvim.

---

### Post by mpaesold on 2011-10-23
Hi!

The problem seems to be related to the global menu app of the netbook remix, AppMenu. You can disable AppMenu for single applications. A line in my bashrc did the trick:
```
export UBUNTU_MENUPROXY=0 gvim
```

I read about this here: [http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html]("http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html")

Good luck!

---

