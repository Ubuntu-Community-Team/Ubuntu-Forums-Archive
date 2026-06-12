---
title: "how to get missing dependencies"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by debd on 2011-04-07
I've been for some time trying to compile the source of AbiWord (I know the package is available; just trying to do it myself ;))  . Now, when I run ./configure it gives the following missing packages.


> No package 'fribidi' found
No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'gobject-2.0' found
No package 'libgsf-1' found
No package 'wv-1.0' found
No package 'cairo-pdf' found
No package 'cairo-ps' found
No package 'pangocairo' found
No package 'gtk+-2.0' found
No package 'gtk+-unix-print-2.0' found
No package 'librsvg-2.0' found

In my /usr/lib folder there are already the glib-2.0 and gtk2.0 folders present. and most of the programs installed in my pc require gtk to run properly. So, I definitely have it installed. Then why is the error?  I see the configure script searches for dep.s in /usr/lib/pkgconfig; which doesn't have the  missing packages. 

does it require those .pc files? and I'll have to install each and every missing packages with apt-get?

Its my first time with compiling a source. I may sound dumb. but I need your answer. :)

---

### Post by debd on 2011-04-07
anyone??

---

### Post by debd on 2011-04-07
ok..so I already got those missing dependencies installed and abiward installation was successful, but 
```
sudo checkinstall
``` didn't work, i.e. installation failed.

I had to do ```
sudo checkinstall --fstrans=0
``` 

but after successful installation (as checkinstall said) abiword isn't opening.

while running the configure script after downloading the dependencies, it said some of the required packages didn't met the version requirements. How am I supposed to prevent apt-get from downloading outdated archives?

---

