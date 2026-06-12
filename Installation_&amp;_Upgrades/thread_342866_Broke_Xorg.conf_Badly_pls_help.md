---
title: "Broke Xorg.conf Badly pls help"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by rjz35 on 2007-01-20
Dear all.

i've turned to the forum, finally, after getting ubuntu-beryl-ati on my Dell61o, working with  it since 1 year now i finally am in a little bit of panic, i trusted my comp. at home also to ubuntu, but failed.

i can not enter the pc anymore. I screwed my xorg.conf badly. tying to run beryl with ati9700pro and aixgl. didn't succeed.

my question is;
is there a way to stop during boot let say the graphical part of ubuntu. like in WINXP press F8 or F6 [i forgot already], My knowled of vi is bad, i really don't know what i'm doing with that program.

pls help

thanks already.

KR
Robbert-jan

---

### Post by an.echte.trilingue on 2007-01-20
When the grub screen pops up, hit the escape button to get into the menu, then boot into rescue mode (single user).

Run ```
sudo dpkg-reconfigure xserver-xorg
``` to fix X.

Take care
-mat

---

