---
title: "pdflatex very slow after update to Ubuntu 20.04 LTS"
date: 2020-06-25
forum: Installation &amp; Upgrades
---

### Post by olivier-joly on 2020-06-25
[COLOR=#000000][FONT=Arial]Hello everyone,[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am using pdflatex to produce daily quantity of pdf on a Apache2 server, but since update to Ubuntu 20.04, it is becomed too slow[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]"time pdflatex -interaction=batchmode --shell-escape 2020061105_BL.tex" give on a 4 year old server under Ubuntu 16.04 LTS :
real    0m1.239s
user    0m1.168s
sys    0m0.040s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]"time pdflatex -interaction=batchmode --shell-escape 2020061105_BL.tex" give on a new i7 16Go RAM under Ubuntu 20.04 LTS, for a same file .tex :
real    0m7,958s
user    0m1,367s
sys    0m6,587s[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]kernel time is 164 time longer .... ? I did not find any solution on Internet, i add same long kernel time on another machine Ryzen 2700. I reinstall many time Ubuntu 20.04 with SSD ou HDD ou HDD+SSD, but no change.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks for your help, to avoid to go back to 18.04 LTS that do not work very well on Ryzen2700.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]A big "THANKS" in advance.[/FONT][/COLOR]

---

### Post by dino99 on 2020-06-26
Which release is used ?
[http://www.tug.org/applications/pdftex/](http://www.tug.org/applications/pdftex/)
[https://linux.die.net/man/1/pdflatex](https://linux.die.net/man/1/pdflatex)

---

### Post by ActionParsnip on 2020-06-26
How many of these do you make and how often, please?

---

### Post by dragonfly41 on 2020-06-27
> ... [COLOR=#000000][FONT=Arial]produce daily quantity of pdf
[/FONT][/COLOR]I also ask is this a batch operation where (for example) only certain fields such as name, address and attributes (images, styles, fonts) are changed in a template and rendered to pdf?

---

