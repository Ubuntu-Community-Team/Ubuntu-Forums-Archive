---
title: "latex on ubuntu"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Orion_PKFD on 2009-12-26
Hi all,

What I need to install LaTex on ubuntu 9.10? I know that Kile is the most used editor but do I need to install something before or something?

I only had used LaTex on Windows Vista. I don't know how to do it on ubuntu.

Best regards

---

### Post by AdotB on 2009-12-26
Ubuntu uses the Texlive distribution of latex.

Installing kile will install its dependencies, which is about 250 MB of latex packages. 

It will also install its kde/qt dependencies as well, so if you dont use any other qt applications, then you might just want to install "texlive" which should install what you need to compile latex documents, and use another ide.

I personally use kile, but
gedit highlights latex, as does vim I think. If you use a text editor that does not have integrated latex buttons like kile does, you will need to run latex from the command line.

Hope that helps you some.

---

### Post by Eider on 2009-12-27
You can give TexMaker a try. It's a very nice program with highlighting and you can compile to pdf etc with a press on the button.

More information:
[http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)

---

### Post by oaxacamatt1 on 2009-12-28
Hi Orion,
I have used Lyx and like it a lot.  I have not used Latex but it installs very easily under synaptic and runs very smoothly under XUbuntu 9.10.

HTH,
Matt

---

### Post by ciric50 on 2010-01-31
I'm trying to get Latex to work, and my document uses the package revtex4 from the American Physical Society. I have the package, but I don't know where to install it. Where is the tex/latex installation for Ubuntu?

---

### Post by ciric50 on 2010-01-31
> **ciric50 said:**
> I'm trying to get Latex to work, and my document uses the package revtex4 from the American Physical Society. I have the package, but I don't know where to install it. Where is the tex/latex installation for Ubuntu?
Found it. Surprisingly you can put revtex right into the Synaptic Package Manager and ti will find it for you (in tetex package).

---

### Post by Abdus on 2010-02-01
> **ciric50 said:**
> I'm trying to get Latex to work, and my document uses the package revtex4 from the American Physical Society. I have the package, but I don't know where to install it. Where is the tex/latex installation for Ubuntu?

If it's just a .sty file it would be enough to keep it in the folder containing your .tex file, as this folder is always scanned by TeX when compiling.

If you want to store it elsewhere, and in the same time NOT in the main TeX tree (which is wise), you can add the location to TeX's searching path - short web search will reveal how it's done, I forget it 2 minutes after I do it, every time. :)

---

### Post by jalirious on 2010-03-30
Deleted. Or at least the intention was there.

---

