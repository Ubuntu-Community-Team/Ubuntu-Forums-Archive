---
title: "Will Live CD allow Minimal or netinstall?"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by os2 on 2015-12-04
I'm looking at the desktop-livecd iso.
Rather than installing the default set of packages is it possible to do a mini/net install using the cd?

Thx

---

### Post by Bashing-om on 2015-12-04
os2; Hello;

No, what you see is what you get, If you want other, there are other install mediums .

[INDENT][INDENT]one size does not fit all
[/INDENT][/INDENT]

---

### Post by os2 on 2015-12-05
Ubuntu mini.iso is a little too Mini. I want to be able to get a very base system going without network access.
I'm looking for something similar to Debian's netinstall.

---

### Post by buzzingrobot on 2015-12-05
Last time I used it, the mini.iso looked and behaved pretty much like Debian's netinstall.  The image includes just enough to bring an ethernet connection up, then it downloads everything else. Eventually, like Debian, it runs tasksel, which lets you choose what's to be installed.

There is an xubuntu-core package ([http://packages.ubuntu.com/wily/xubuntu-core](http://packages.ubuntu.com/wily/xubuntu-core)) that doesn't install much at all.That won't meet your "without network access" requirement since it's intended to be installed via the mini.

---

### Post by sudodus on 2015-12-05
If you want almost the same functions, but have more included in the iso file (compared to the mini.iso), you can ***start from the Ubuntu Server iso file***. If you ***select no server package***, 'only reboot', you will get a very basic text-screen system without any graphical desktop environment.

---

### Post by os2 on 2015-12-06
> **sudodus said:**
> If you want almost the same functions, but have more included in the iso file (compared to the mini.iso), you can ***start from the Ubuntu Server iso file***. If you ***select no server package***, 'only reboot', you will get a very basic text-screen system without any graphical desktop environment.

Perfect @sudodus. Exactly what I was after.

To the previous poster. Ubuntu mini isn't the same as Debian netinstall. Mini gets the base system using a network connection. Debian netinstall can do the same except it also has a base system. 

Perfect if you want to get a base system going without having a network connection to start with.

---

