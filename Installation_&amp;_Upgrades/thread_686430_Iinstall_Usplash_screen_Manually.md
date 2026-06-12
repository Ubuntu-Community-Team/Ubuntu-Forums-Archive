---
title: "Iinstall Usplash screen Manually"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by SoberWarlock on 2008-02-03
I'm looking for a way to do everything manually in Ubuntu like customizing splash screens so that I can have a better experience with files and stuff. I don't want to depend on programs all the time since most of the time they screw me over :mad: So is there a way I can do this when I download a customized usplash screen in Gnome Look?

---

### Post by Partyboi2 on 2008-02-04
You could try one of these
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
[http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml](http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml)
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

---

### Post by mmpatels on 2008-02-17
Hi all

im new to linux so ur help vl b highly appreciated

when i try to run command

gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-mine.c -o usplash-mine.o

i get a error

usplash-mine.c:1: error: expected '=', ',', ';', 'asm' or '___attribute__' before 'opening'

can some 1 help me to solve this problem

thx
mmp

---

### Post by y-lee on 2008-02-17
> **mmpatels said:**
> 
when i try to run command

gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-mine.c -o usplash-mine.o

i get a error

usplash-mine.c:1: error: expected '=', ',', ';', 'asm' or '___attribute__' before 'opening'



I've never tried to created my own usplash but it appears to me something is wrong with your file usplash-mine.c, did you follow the directions at [Change Ubuntu Bootsplash]("http://news.softpedia.com/news/Change-Ubuntu-Bootsplash-Theme-55237.shtml") ?

In particular did you use the command 

```
pngtobogl usplash-mine.png > usplash-mine.c
```

to create the file usplash-mine.c? If so notice comment #2 on softpedia's page:

> the command:
pngtobogl usplash-artwork.png > usplash-artwork.c
is supposed to be
pngtousplash usplash-artwork.png > usplash-artwork.c

At least in Kubuntu 7.10

---

