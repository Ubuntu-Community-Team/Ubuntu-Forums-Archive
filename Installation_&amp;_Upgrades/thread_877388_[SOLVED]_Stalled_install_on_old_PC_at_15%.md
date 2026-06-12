---
title: "[SOLVED] Stalled install on old PC at 15%"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by Gopi Grut on 2008-08-01
I'm trying to install xubuntu on a dell inspiron 3500 pc with a pentium II 264.7MHz 192M 169MB/s and Intel i440BX.

It stalls when loading the program at 15%. I've seen other threads for this but no solutions that work.

I've tried installing the alternate and it stalls out as well. I've tried installing in safe mode - same problem.

Any suggestions? What is the process for installing through the text interface? Would that cut down on memory use and let things move through?

Gopi :( confused

---

### Post by dominiquec on 2008-08-01
Might be the low memory of your system.  Try using the Alternate Install CD but specify Command-Line Only system.  Take a look at [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems).

---

### Post by Gopi Grut on 2008-08-01
your recomendation worked for loading xubuntu on my old pc, thanks! any idea on how to get it to start up? it seems to want to be in programming mode and i just want to use it.

---

### Post by Partyboi2 on 2008-08-01
What you have installed at present is only the command line system, you would need to install a graphical environment. If you look at the link dominiquec provided, further down the page you will see how to install additional components to get a working desktop.

On that webpage start at "installing xorg" then choose a windows manager etc

---

### Post by dominiquec on 2008-08-02
You're welcome, GG.

This is a little less complete than the HOWTO (as Partyboi pointed out, more instructions below), but in case you're interested how I set my system up: [http://ubuntuliving.blogspot.com/2008/06/minimalist-ubuntu.html](http://ubuntuliving.blogspot.com/2008/06/minimalist-ubuntu.html)

---

### Post by troykd on 2008-08-02
I had the same problem today.  Gave my mother an old laptop awhile back and she'd been running Kubuntu on it.  Well, it got a bit messed up so I went to install Xubuntu on it today, a fresh Hardy Heron install.  It stalled at 15% also.  It did install from the Alternate CD though without a hitch.

---

