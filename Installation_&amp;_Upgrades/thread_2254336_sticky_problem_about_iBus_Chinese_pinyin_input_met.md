---
title: "sticky problem about iBus Chinese pinyin input method"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by elim-qiu on 2014-11-26
All the great efforts towards the changes of ibus pinyin from ubuntu 12 to 14 simply guarantee one thing: miss-interpreter Chinese pinyin inputs.

Bug reports like iBus pinyin not working, Chinese Character Candidates not appearing etc didn't address the fatal issue with iBus pinyin:

It interpreters your pinyin entry into an array of guess_units, adding more letters typically to make sure the guess_unit is the pinyin of some Chinese Char. The logic of such interpretation, seem can guarantee 99% wrong output hence guarantee itself 100% a piece of junk.

I wonder how such piece of software gets tested. You enter some pinyin, it surely produce wrong output (yes in Chinese chars) very quickly and smoothly.

I found no post in Ubuntu Chinese programming community saying this can be fixed by os installation , updating or lib/software re-installaton/re-configuration etc. The community seem to accept it as hopeless and turns to SOGo pinyin etc.

---

