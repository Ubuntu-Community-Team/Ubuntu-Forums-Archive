---
title: "Why changing system language does not lead to immediate change?"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by ambeginnersearchinginfo on 2010-10-31
Using Ubuntu 10.10 CD live system.
Installing Korean as system language, keeps some English remaining.
Did I something wrong or is not everything translated?


  Choosing system language in the start menu of Ubuntu and/or changing the system language can lead to

1) a virtual keyboard / on-screen keyboard showing on the keys another language than that one which appears on the screen while writing (input language )and 
( yet not tested for Ubuntu, but in Kubuntu it does not work)

2) even the language of what is displayed as input on the screen can be different from the language of the same input which receives the application, 
( at least in Kubuntu, yet not tested for Ubuntu)

e.g. typing a word in the entry of an online dictionary can lead to the effect, that what you see in the entry of the online dictionary as your input is another language than the language of the word which will be actually translated and

3) it can lead to single windows with a mess and mixture of languages. (also in Ubuntu)

I don't understand why this is necessary. If the translations are in a central array/table like the tables for the keyboard layouts
than the system can just map to the new translations table at the moment when the system language is changed like the change of the keyboard laxout, and
the system can provoke, that the virtual keyboard and the active window load the new translations and display them.
Everytime a window is activated or reloaded, the window could check whether or not the system language has changed and load the new translations and display them.

Why there is a mess and why is this so difficult fix?
Maybe I know too little, but maybe there will be an answer and a suggestion to improve Ubuntu.

---

