---
title: "Upgrade from Oneiric to Precise causes Aptitude issues"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by meowsus on 2012-10-22
Hey guys,

I was running Lubuntu Oneiric on my work machine for a long time, since I was worried about an upgrade causing me to lose a lot of time fixing up the issues that I've seen before by doing a full version upgrade.

One day last week I was bored and I decided to do the upgrade to Precise. It went very well and I'm very happy, but now when I run **sudo aptitude dist-upgrade** there are a lot of unresolved dependencies.

I'm very nervous about accepting the solution Aptitude proposes. Can someone look over this list and give me some kind of idea as to (a) what's going on here, and (b) if it seems like I won't be totally screwed by accepting the dependency resolution?

[http://pastie.org/pastes/5098612/text]("http://pastie.org/pastes/5098612/text")

Thanks in advance!

---

### Post by dino99 on 2012-10-22
first, if PP is already upgraded, then you should not use dist-upgrade again, its no sense.
then after each dist-upgrade, there is of course lot of oldish thinks left behind, so clean the room:

- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

note: better use apt-get than aptitude, and never use both as they built their own incompatible index.

you might also watch your /etc/apt/sources.list to be sure that oldish entries are gone (like ppa pointing to something else than PP)

---

### Post by meowsus on 2012-10-22
Hey dino99,

Thanks for the tips. Worked like a charm!

Curt

---

