---
title: "Installing Winedt and MikTex"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by krugman on 2006-08-02
Hello!

I tried to install Winedt with wine, and it worked perfectly. the thing is, it does not recognize my miktex install, so it is basically useless for the moment! I have tried to locate it at diverse places (i.e., C:\texfm...) but winedt does not recognize it.

Has anybody been able to successfully use it???

Thanks!

---

### Post by tkjacobsen on 2006-08-02
Kile is a very good altarnative to winedit. (I thing it is better).
Just install tetex and kile: 
```
sudo apt-get install tetex-bin tetex-base tetex-extra kile
```

tetex is the linux version of latex, while miktex is the windoze version

It is a good idea to get used to linux native tools. Else you can just stay with windoze.

---

### Post by FryerFox on 2006-08-02
I have to agree about Kile. It's quite decent, and I used to use winedt myself. 

You may want to check out this thread for more info:
[http://ubuntuforums.org/showthread.php?t=201947](http://ubuntuforums.org/showthread.php?t=201947)

---

### Post by FryerFox on 2006-08-02
.

---

### Post by krugman on 2006-08-03
Ok, thanks I will have a look at Kile.
Gedit seems good with Latex also so I will see!
The thing is, Winedt was very very good, user friendly but customizable, with a spellchecker integrated...this is awesome since I write in English and this is not my native language!
I think Kile does not have a spellchecker right?

---

### Post by krugman on 2006-08-03
Also, isn't Tetex slightly outdated?

---

### Post by tkjacobsen on 2006-08-03
Kile indeed has integrated spell checking (in the tools menu).. Kile also is very configurable and has a very nice inverser search feature when using .dvi files (if configured probably).  

And tetex works great. I have written 20+ larger projects in tetex with no problems in the larst year.

---

### Post by tkjacobsen on 2006-08-03
You could also try emacs with preview-latex

---

### Post by krugman on 2006-08-03
Ok I will have a go at kile, but I have discovered Texmaker and it really looks great!
But I have some trouble with the configuration since it does not want to pdflatex my preject. I guess he right path is not entered, but I don't know what to do yet...
BTW, tetex is already installed in Ubuntu, so I don't need to do anything about that right?

---

### Post by mov22 on 2006-08-04
IMHO, WinEdt is the best choice under Linux too. (Emacs, vim come from the times when one can spend years studying how to work with a program; gedit, tea miss many features of WinEdt; Kile is better in principle than WinEdt but it is still only a funny toy as long as it lacks on-the-fly spellchecking).

WinEdt works great with last versions of Wine and it works smoothly with tetex. Some months ago I wrote (in Russian) a short howto on usage of Wine+WinEdt+tetex:
[http://www.opennet.ru/base/X/wine_wineedit.txt.html](http://www.opennet.ru/base/X/wine_wineedit.txt.html)

If anybody is interested I could translate the howto to English.

---

### Post by krugman on 2006-08-05
well, kile also has spellchecking abilities unless I am mistaken. But maybe not "as you write" spellchecking since you have to do this manually...

Well, I would be interested in the How-to since I was not able to make Winedt work with tetex. My main problem was to know how to configure the different tools, like PDFLATEX...for Winedt to find the binaries...I didn't know how to set the path, since that's basically a windows stuff, I didn't know if it would recognize something like /usr/local/tetex/Latex...or something like that...

---

### Post by mov22 on 2006-08-07
I have put the howto in English to 
[http://mov.mail15.com/winedt_wine_tetex.html](http://mov.mail15.com/winedt_wine_tetex.html)

Btw, there is a good guide how to make Wine look better
[http://www.justlinux.com/forum/showthread.php?t=141207&goto=nextoldest](http://www.justlinux.com/forum/showthread.php?t=141207&goto=nextoldest)

---

### Post by findik1 on 2007-09-02
> **mov22 said:**
> IMHO, WinEdt is the best choice under Linux too. (Emacs, vim come from the times when one can spend years studying how to work with a program; gedit, tea miss many features of WinEdt; Kile is better in principle than WinEdt but it is still only a funny toy as long as it lacks on-the-fly spellchecking).

WinEdt works great with last versions of Wine and it works smoothly with tetex. Some months ago I wrote (in Russian) a short howto on usage of Wine+WinEdt+tetex:
[http://www.opennet.ru/base/X/wine_wineedit.txt.html](http://www.opennet.ru/base/X/wine_wineedit.txt.html)

If anybody is interested I could translate the howto to English.

Yes, please would you please translate for us. I believe winedt is better than Kile or any other linux tools. Winedt has online spell checking and autoarrange wrapping. Kile has also wrapping not online spelling, but wrapping does not work as good as Winedt.

---

### Post by henriette_holm on 2007-09-03
Yes, please please do. I miss Winedt.

/Henriette

---

### Post by krugman on 2007-09-04
Guys, you should definitely learn Emacs: I also started with winedt under Windows, but after switching to linux, I switched to Emacs and I really don't regret it.
It has a bit steeper learning curve than other stuff, but it is really a much more powerful editor than winedt. There are a lots of configuration files examples around the web, which is very helpful.
 
The only asset of Winedt plus MikTeX is that you can easily (and automatically) add packages to your LaTeX installation.

---

### Post by findik1 on 2007-09-10
> **mov22 said:**
> I have put the howto in English to 
[http://mov.mail15.com/winedt_wine_tetex.html](http://mov.mail15.com/winedt_wine_tetex.html)

Btw, there is a good guide how to make Wine look better
[http://www.justlinux.com/forum/showthread.php?t=141207&goto=nextoldest](http://www.justlinux.com/forum/showthread.php?t=141207&goto=nextoldest)

great! thanks!

---

