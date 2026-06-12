---
title: "pdflatex is significantly slower in 20.04"
date: 2022-02-10
forum: Installation &amp; Upgrades
---

### Post by VadimRadionov on 2022-02-10
Hi everyone,
I have the same issue as in this thread   [https://ubuntuforums.org/showthread.php?t=2446151](https://ubuntuforums.org/showthread.php?t=2446151)
On X1 Gen 9 with ubuntu 20.04 my 14000-pages file compiles in 14 min, while on the older X1 Gen 4 with ubuntu 16.04 in just 2 minutes.  
Do you have any suggestions?
Thank you in advance

-------------

real    14m23,594s
user    1m57,165s
sys    12m19,631s

pdfTeX 3.14159265-2.6-1.40.20 (TeX Live 2019/Debian)
kpathsea version 6.3.1
Copyright 2019 Han The Thanh (pdfTeX) et al.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX source.
Primary author of pdfTeX: Han The Thanh (pdfTeX) et al.
Compiled with libpng 1.6.37; using libpng 1.6.37
Compiled with zlib 1.2.11; using zlib 1.2.11
Compiled with xpdf version 4.01



vs

[FONT=Arial]real 2m15.146s[/FONT]
[FONT=Arial]user 2m9.087s[/FONT]
[FONT=Arial]sys 0m5.726s
[/FONT]
[FONT=Arial]pdfTeX 3.14159265-2.6-1.40.18 (TeX Live 2017/Debian)[/FONT]
[FONT=Arial]kpathsea version 6.2.3[/FONT]
[FONT=Arial]Copyright 2017 Han The Thanh (pdfTeX) et al.[/FONT]
[FONT=Arial]There is NO warranty.  Redistribution of this software is[/FONT]
[FONT=Arial]covered by the terms of both the pdfTeX copyright and[/FONT]
[FONT=Arial]the Lesser GNU General Public License.[/FONT]
[FONT=Arial]For more information about these matters, see the file[/FONT]
[FONT=Arial]named COPYING and the pdfTeX source.[/FONT]
[FONT=Arial]Primary author of pdfTeX: Han The Thanh (pdfTeX) et al.[/FONT]
[FONT=Arial]Compiled with libpng 1.6.29; using libpng 1.6.29[/FONT]
[FONT=Arial]Compiled with zlib 1.2.8; using zlib 1.2.8[/FONT]
[FONT=Arial]Compiled with poppler version 0.41.0[/FONT]

---

