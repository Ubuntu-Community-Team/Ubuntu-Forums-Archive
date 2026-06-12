---
title: "support of different locales (languages) under kubuntu"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by lefsha on 2008-11-09
Hello all,

I just installed Kubuntu 8.10 and have no idea how to make possible to use different languages under kde and console.

With 8.04 I didn't have suche a problem.

What I did:
System settings - > Regional & Languages - > Add Language etc

What I've got:

My console programs use russian locale... why? The system language is
still english...

Under root it still in english.
In KDE i'm not able to switch between languages. I'm normally get used to use KKBSwitch for that.

Some programs in KDE like Adept use mixt of russian and english.

My xorg.conf is empty...


Any Idea?

---

### Post by CptPicard on 2008-11-09
I seem to have a problem which is similar. I upgraded to Ibex, and all of a sudden under KDE the LANGUAGE variable is always set to "fi" for Finnish, although in my .bash_profile I set it to "en" and even in KDE settings language is indeed set to English. So now I have a really annoying situation where some applications decide to be in Finnish while most of it is in English, and most annoyingly tools like make and gcc give their output in Finnish, which for a programmer is just totally annoying.

Under console outside of X and KDE, language is English as I want it to be, so this is probably something KDE-specific... I just don't seem to be able to figure out where the LANGUAGE=fi setting comes from that overrides what I have in .bash_profile :(

EDIT: Ok, so managed to kill all the Finnish by totally removing Finnish support from KDE... so now under Konsole LANGUAGE=en_US. It's a bit weird because in KDE's language settings English was at top of the list, and Finnish was 2nd... doesn't it say there that apps should use the first language in the list?

---

### Post by lefsha on 2008-11-10
Are you able to switch between locales?

---

