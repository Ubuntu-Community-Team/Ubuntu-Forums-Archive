---
title: "Fedora 2 Ubuntu trouble &gt;.&gt;"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by twiistedkaos on 2006-05-13
Well, as the topic stated, I am / was a fedora user for about 5 months but I decided to give Ubuntu a try, infact I am on ubuntu right now. I did notice that even after the update that noticed me on my first boot that I am still using gnome 2.12.1 instead of the newest verison 2.14.1 which is the version I would much rather use! Also my firefox verison after the update is 1.0.8 and the newest version is 1.5.3! I suppose my question is "What's up the the Ubuntu updates?" are they that far behind? Now I am completely new to debian based distro's, I am very use the RPM based, now this move has left me majorly confused, so if you have any help on how to upgrade to gnome 2.14.1 and the newest version of firefox I'd much appreciate it!

---

### Post by user1397 on 2006-05-13
i'm not sure about gnome, i do know that 2.14.1 comes stnadard with dapper
as for firefox 1.5, there are several options.  
you can use automatix to easily install firefox and many other things:
[http://www.ubuntuforums.org/showthread.php?t=138405]("http://www.ubuntuforums.org/showthread.php?t=138405")
or you can use the wiki guide:
_wiki.ubuntu.com/FirefoxNewVersion_,
and then you might want to look at the restricted formats page to let firefox view java, flash, windows media/quicktime files, using this guide:
_wiki.ubuntu.com/RestrictedFormats_
(of course you can also use automatix for the restricted formats, it comes bundled with the installation of firefox)

---

### Post by louis_nichols on 2006-05-13
The solution to the firefox issue is [here]("https://wiki.ubuntu.com/FirefoxNewVersion?"). Many answers can be found on thwe wiki.

As for the rest, I also came from fedora and was puzzled at first just like you. I haven't found an official answer, like a faq or smth, to this (yet) but it seems to be that, after a release, Ubuntu only offers security *updates* to the packages included in that release, and not *upgrades.*. For example, when Breezy was launched, Firefox was 1.0.7 and now, in the repos it is at 1.0.8 because of security fixes.

The [backports project]("https://wiki.ubuntu.com/UbuntuBackports"), which is community maintained, not officially supported project aims to adapt new versions of software to work with previously released versions of Ubuntu.

---

### Post by twiistedkaos on 2006-05-13
From what it seems is I am stuck with gnome 2.12.1 until a new version of ubuntu is released? Another question though, when the new version of ubuntu is released to I have to do a full reinstall again, IE: download the iso and install? Or is it done though an update? THe main reason I moved from fedora is the fact that I had to downlaod 5+ cd's everytime they released a new version, which is quite annoying.

---

### Post by turbojugend_gr on 2006-05-13
No that's why ubuntu rock, i was SuSE user and i had similar probs. Not anymore. When the Dapper Drake is done (which should be in June) you can update to it, it's rather slow but no trouble. In fact it's rumored that Dapper will have a graphical update also added to the apt-get one (through terminal). As for the deb's feel free to ask, these folks are great at giving help, that's what I learned in the Past  month and a half.

---

### Post by louis_nichols on 2006-05-13
[QUOTE=turbojugend_gr]No that's why ubuntu rock, i was SuSE user and i had similar probs. Not anymore. When the Dapper Drake is done (which should be in June) you can update to it, it's rather slow but no trouble. In fact it's rumored that Dapper will have a graphical update also added to the apt-get one (through terminal). As for the deb's feel free to ask, these folks are great at giving help, that's what I learned in the Past  month and a half.[/QUOTE]

well... most folks wouldn't go as far as to say "no trouble", but it should work pretty good. A search for some keywords on this matter will certainly reveal some more or less successful experiences.

It works for the most part, but some details might not go perfectly ok (after all, there is an AWFULL lot of details that can go wrong). The process of updating itself, though, is as easy as editing a file as root and entering a command in terminal. Well, at leats now. Perhaps it will get even simpler in the future, as turbojugend_gr says.

EDIT: typo

---

### Post by turbojugend_gr on 2006-05-13
The no trouble thing is compared to having your disk backuped-formatted-ubuntu installed and your configurations starting from ZERO. As far as I am concerned, that can be called some trouble. Though your point on its own is correct.

---

