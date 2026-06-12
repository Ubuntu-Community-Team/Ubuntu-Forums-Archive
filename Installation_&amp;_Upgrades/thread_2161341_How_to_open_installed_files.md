---
title: "How to open installed files ?"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by Yasminp on 2013-07-10
I have installed Gnuplot , Latex and fortran 95 compiler.But i am not able to find any of these files to run them. Plz give some suggestions.

---

### Post by steeldriver on 2013-07-10
Hello and welcome to the forum

Those are all command line programs (although latex would typically be run from inside a graphical front end) - you just run them by typing the executable name (+ arguments, if applicable) in a terminal.

What exactly are you trying to do? plot stuff? write documents? compile code? if you give us specific examples we can help get you started

---

### Post by bokgeneraal on 2013-07-10
I think gnuplot is a program or library used by programs such as octave for plotting graphs. So to use install something like octave or qtoctave. The same can be said of Latex which is a typesetting language and Fortran 95 compiler which is used to compile fortran source code.;)

---

### Post by steeldriver on 2013-07-10
actually gnuplot has a standalone command interpreter right out of the box (although it *can* be used by other programs)

---

### Post by VMC on 2013-07-10
Try:```
[COLOR=#000000]gnuplot> load "all.dem"[/COLOR]
```

To find any installed program, or to give a hint of its name. Try, for example:
```
sudo dpkg --get-selections|grep office
```

---

