---
title: "Octave and gnuplot"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by joebanana on 2008-05-05
Octave doesn't find gnuplot although I installed it and can run it. When I installed it in 7.10 it worked with no problems. Here is what I get in octave:

```
octave:5> plot(x,y)
Expected X11 driver: /usr/lib/gnuplot/gnuplot_x11
Exec failed: No such file or directory
See 'help x11' for more details
Expected X11 driver: /usr/lib/gnuplot/gnuplot_x11
Exec failed: No such file or directory
See 'help x11' for more details

```

Please help

---

### Post by joebanana on 2008-05-05
Could somebody please just check if he has the same problem after installing octave and gnuplot.

---

### Post by kurakusan on 2008-05-05
DIDO. 

octave:1> plot(1:9)
Expected X11 driver: /usr/lib/gnuplot/gnuplot_x11
Exec failed: No such file or directory
See 'help x11' for more details
octave:2> Expected X11 driver: /usr/lib/gnuplot/gnuplot_x11
Exec failed: No such file or directory
See 'help x11' for more details

---

### Post by jtlanzi on 2008-06-09
I installed gnuplot followed by octave and suffered the exact same symptoms.

Has this been resolved yet?

---

### Post by runescape1143 on 2008-08-31
sudo apt-get install gnuplot-x11 should do the trick...

---

