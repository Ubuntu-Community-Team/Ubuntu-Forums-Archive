---
title: "fonts problem --- output of xlsfonts"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by rarew on 2011-09-03
Hi it seems that the output of "xlsfonts" has been changed in 11.04, or less fonts are installed. 

For example, in 10.04, the output format is like
adobe-times-bold-i-normal--12-120-75-75-p-68-iso10646-1

but in 11.04, output are something like
-adobe-times-bold-i-normal--0-0-0-0-p-0-iso8859-1

i.e., I can not find things like "12-120-75-75" anymore. 

I actually know nothing about fonts. So I do not know whether this means a format change, or means I missed any fonts. Can anybody help me? Much appreciated!


The reason for asking is because, the error message in a software I am using is


init_xfonts: WARNING ... font *Times*medium-r*24* not found
init_xfonts: WARNING ... font *Times*medium-r*34* not found
init_xfonts: WARNING ... font *Times*bold-r*18* not found
init_xfonts: WARNING ... font *Times*bold-r*24* not found
init_xfonts: WARNING ... font *Times*bold-r*34* not found
init_xfonts: WARNING ... font *Times*medium-i*18* not found
init_xfonts: WARNING ... font *Times*medium-i*24* not found
init_xfonts: WARNING ... font *Times*medium-i*34* not found
init_xfonts: WARNING ... font *Times*bold-i*18* not found
init_xfonts: WARNING ... font *Times*bold-i*24* not found
init_xfonts: WARNING ... font *Times*bold-i*34* not found
init_xfonts: WARNING ... font *symbol*12* not found
init_xfonts: WARNING ... font *symbol*18* not found
init_xfonts: WARNING ... font *symbol*24* not found
init_xfonts: WARNING ... font *symbol*34* not found

---

### Post by kerry_s on 2011-09-03
install lubuntu-restricted-extras it will add ms fonts & other restricted stuff.

---

### Post by rarew on 2011-09-03
> **kerry_s said:**
> install lubuntu-restricted-extras it will add ms fonts & other restricted stuff.

I did that, and it does not work.

Actually the ones I quoted from 10.04 was installed by default.

---

### Post by rarew on 2011-09-03
> **rarew said:**
> Hi it seems that the output of "xlsfonts" has been changed in 11.04, or less fonts are installed. 

For example, in 10.04, the output format is like
adobe-times-bold-i-normal--12-120-75-75-p-68-iso10646-1

but in 11.04, output are something like
-adobe-times-bold-i-normal--0-0-0-0-p-0-iso8859-1

i.e., I can not find things like "12-120-75-75" anymore. 

I actually know nothing about fonts. So I do not know whether this means a format change, or means I missed any fonts. Can anybody help me? Much appreciated!


The reason for asking is because, the error message in a software I am using is


init_xfonts: WARNING ... font *Times*medium-r*24* not found
init_xfonts: WARNING ... font *Times*medium-r*34* not found
init_xfonts: WARNING ... font *Times*bold-r*18* not found
init_xfonts: WARNING ... font *Times*bold-r*24* not found
init_xfonts: WARNING ... font *Times*bold-r*34* not found
init_xfonts: WARNING ... font *Times*medium-i*18* not found
init_xfonts: WARNING ... font *Times*medium-i*24* not found
init_xfonts: WARNING ... font *Times*medium-i*34* not found
init_xfonts: WARNING ... font *Times*bold-i*18* not found
init_xfonts: WARNING ... font *Times*bold-i*24* not found
init_xfonts: WARNING ... font *Times*bold-i*34* not found
init_xfonts: WARNING ... font *symbol*12* not found
init_xfonts: WARNING ... font *symbol*18* not found
init_xfonts: WARNING ... font *symbol*24* not found
init_xfonts: WARNING ... font *symbol*34* not found

It is solved. 
I did installed the following programs (by time order). Not sure which one did the trick

xfstt
t1-xfree86-nonfree
ttf-xfree86-nonfree
ttf-xfree86-nonfree-syriac
xfonts-75dpi
xfonts-100dpi
ttf-linux-libertine
texlive-doc-en (2009-2)
ttf-linex (2.2-4)
texlive-lang-ukenglish (2009-3)
xfonts-bolkhov-75dpi (1.1.20001007-6ubuntu3)
xfonts-bolkhov-cp1251-75dpi (1.1.20001007-6ubuntu3)
xfonts-bolkhov-isocyr-75dpi (1.1.20001007-6ubuntu3)
xfonts-bolkhov-koi8r-75dpi (1.1.20001007-6ubuntu3)
xfonts-bolkhov-koi8u-75dpi (1.1.20001007-6ubuntu3
mathematica-fonts (12)
cm-super-minimal (0.3.4-3)
cm-super-x11 (0.3.4-3)
ttf-unfonts (1.0.3.is.1.0.1-0ubuntu1)
ttf-unfonts-extra (1.0.3.is.1.0.1-0ubuntu1)

---

