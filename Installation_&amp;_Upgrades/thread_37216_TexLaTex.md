---
title: "Tex/LaTex?"
date: 2005-05-26
forum: Installation &amp; Upgrades
---

### Post by agger on 2005-05-26
How do I install Latex on my Hoary installation?

Synaptic has lots of Latex-related packages but no Latex or Tex package that i can find. I'm using the preinstalled repositories + the ones mentioned in [www.ubuntuguide.org](www.ubuntuguide.org)

Thanks a lot in advance,
Carsten

---

### Post by ow50 on 2005-05-26
These should get you started:
tetex-base
tetex-bin
tetex-extra
latex-ucs

tetex is the tex/latex system. latex-ucs is a package that allows you to use UTF-8 with latex, see [another thread](http://www.ubuntuforums.org/showthread.php?t=31039) on that.

---

### Post by Alexander Kirillov on 2005-05-26
[QUOTE=agger]How do I install Latex on my Hoary installation?

Synaptic has lots of Latex-related packages but no Latex or Tex package that i can find. I'm using the preinstalled repositories + the ones mentioned in [www.ubuntuguide.org](www.ubuntuguide.org)

Thanks a lot in advance,
Carsten[/QUOTE]
 Install tetex-base, tetex-bin, tetex-doc, tetex-extra. It installs all the tools you need (including latex, xdvi, and dvipdfm). 

I also recommend Kile as a frontend. It is a KDE app, so it will require quite a few other things (and to make it work normally, you will also need kdvi, kviewshell, and kate - which are not listed as dependencies) - but it is worth it.

---

### Post by arrizaba on 2005-05-26
Well, Kile is nice (I actually know personally the main developer, so I should make some publicity on his behalf  ;-)  ).
But it is [COLOR=RoyalBlue]KDE[/COLOR], so it will work better on [COLOR=RoyalBlue]Kubuntu[/COLOR] than in the [COLOR=DarkOrange]Gnome[/COLOR] based Ubuntu. If you like using Vi, then you should definitely install the vim-latex suite, that you can find at:
[COLOR=Blue]
[http://vim-latex.sourceforge.net/](http://vim-latex.sourceforge.net/)[/COLOR]

---

### Post by kb00heda on 2005-05-26
Another alternative is of course emacs. But I prefer kile too. It is really nice once you get to tweak it a bit. Actually I use kate when writing programs in MATLAB or Fortran, and find it to be OK.

---

### Post by agger on 2005-05-26
> **arrizaba]Well, Kile is nice (I actually know personally the main developer, so I should make some publicity on his behalf   said:**
> KDE[/COLOR], so it will work better on [COLOR=RoyalBlue]Kubuntu[/COLOR] than in the [COLOR=DarkOrange]Gnome[/COLOR] based Ubuntu. If you like using Vi, then you should definitely install the vim-latex suite, that you can find at:
[COLOR=Blue]
[http://vim-latex.sourceforge.net/](http://vim-latex.sourceforge.net/)[/COLOR]

Thanks for the kind response - tetex-base is downloading right now!

I'm running Gnome and as a bit of a newbie to Linux, I think I'll try Kile when I'm a bit more comfortable using KDE apps (or have tried out Kubuntu).

Vi is actually my favorite editor, so I think I'll start with the vim-latex package.

thanks again,
Carsten.

--
[http://www.modspil.dk](http://www.modspil.dk)
- fordi tiden kræver et MODSPIL!

---

### Post by kb00heda on 2005-05-26
Sounds like the thing to do (I started off using emacs since that was the editor I was familiar with). Browsing through the contents of the TeX sections in synaptic might then give hints on other useful packages.

---

