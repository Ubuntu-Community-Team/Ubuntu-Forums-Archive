---
title: "tetex + ptex problem on Edgy"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by jishinonnix on 2006-12-07
Hi,

I'm install tetex and ptex-related packages on Edgy in order to make Japanese latex document. After a few problems about dependencies, I got it installed.

platex compiled EUC Japanese tex file ok, but when I tried to make pdf from dvi with dvipdfm,dvipdfmx , it pulled out errors and the pdf file did not show Japanese correctly.

> jishin@ibm:~/Devel/LaTeX$ dvipdfm jpex

jpex.dvi -> jpex.pdf
[1
TFM file error (ec < bc)


Output file removed.

jishin@ibm:~/Devel/LaTeX$ dvipdfmx jpex
jpex.dvi -> jpex.pdf
[1
** WARNING ** No character mapping available.
 CMap name: H
 input str: <2c>
]
6996 bytes written


To export Japanese fonts to pdf, I install below packages 
> % sudo apt-get install gs-cjk-resource
% sudo apt-get install cmap-adobe-cns1 cmap-adobe-gb1
% sudo apt-get install cmap-adobe-japan1 cmap-adobe-japan2

After installed, defoma complained somethings 
> 
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 108.

Can't exec "/usr/bin/mkcfm": No such file or directory at /var/lib/defoma/scripts/x-ttcidfont-conf.defoma line 791.


Any helps would be appreciated.

TIA

---

