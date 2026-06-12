---
title: "Input method problem in Lucid"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by lanig on 2010-04-24
Hi all,

I have been using a french ubuntu system with japanese support for years without any problem.
Trouble started to appear last automn with Karmic. Ibus didn't remplace scim and some applications like firefox were crashware with scim enabled. Emacs to had a minor problem and refused to write accentuated lettres like ê with scim enabled. So I resorted to have a no_scim script 
#!/bin/bash


export XMODIFIERS=""
export GTK_IM_MODULE=""
export XIM_PROGRAM=""
export QT_IM_MODULE=""

exec $@

to launch these applications.

To get out of this problems, I installed today lucid, removed all scim and uim stuff and choosed ibus as the input method. 
As a result, no japanse input is available now, though anthy is choosen in the ibus pref list and emacs still refuses to write accentuated lettres.

Thanks for your help,

Alain

---

### Post by chandra on 2010-07-21
Have you had any luck solving your problem?

I have found scim/skim to not work in Lucid and also note that one or both have been removed from the standard distribution. I wonder if ibus is the replacement, and if so, how to make it work for Indic and Latin scripts.

Thanks.

---

