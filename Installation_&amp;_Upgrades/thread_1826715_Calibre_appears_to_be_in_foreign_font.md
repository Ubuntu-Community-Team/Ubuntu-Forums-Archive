---
title: "Calibre appears to be in foreign font"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by hey.you on 2011-08-16
Hi,

I have been trying to install Calibre, but it appears to be in a foreign font that I can't read. I know how to select the language, but after selecting what I think is English or any other language (I have tried them all) the font does not change. Can someone tell me how to fix this? I have not been able to find a solution anywhere or even the same problem mentioned anywhere.

I am trying to install it in 10.10 and have used the Software Centre and Terminal. I have deleted everything that mentions Calibre between install. I have attached images of Calibre.

Thank you,

Kelly

---

### Post by boubalos on 2012-05-18
Check your locale setup
Run qtconfig-qt4 to setup the correct font, if you have not install  qtconfig-qt4, try "sudo apt-get install qt4-qtconfig"

for example
> export LC_CTYPE=en_US.utf8
> qtconfig-qt4

---

