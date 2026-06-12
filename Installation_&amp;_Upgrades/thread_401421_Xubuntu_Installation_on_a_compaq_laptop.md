---
title: "Xubuntu Installation on a compaq laptop"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by aquavitae on 2007-04-04
I'm trying to install xubuntu on an old compaq presario laptop using the alterate cd. It gets to 65% in the installation (Configuring anthy) and it freezes. I've tried it on another computer and it worked fine. The last message logs on console 4 are 

debconf: obsolete command TITLE Configuring anthy called
In-target: updating anthy.dic

I understand anthy is something to do with japanese so its not even something i want. Is this something to do with my hardware? Is there a way to avoid installing packages i don't want?

---

### Post by carverj on 2007-04-05
I am having the same trouble installing Xubuntu fiesty Beta to an old IBM laptop(thinkpad with only 64MB RAM).
Are you using a previous versions alternate CD?

---

### Post by Brendantb on 2007-04-05
Hi,

How much RAM do you have in the laptop?

---

### Post by carverj on 2007-04-05
64MB RAM only
Happy Easter all!!

---

### Post by aquavitae on 2007-04-13
Sorry, been away so I haven't seen your replies.  I was using Edgy aternate CD.  I don't have much ram (64 I think, can't remember offhand!) which is why I took the alternate cd.  It did eventually work - I left it overnight and it finished 12hrs later.  Long way round, but at least its installed!

---

### Post by Brendantb on 2007-04-13
Hi, 

It's good to see that you have completed the installation. I don't have enough information on the exact laptop model that you have to know if it is easily upgradeable, but if there is a free slot, it would be highly recommended to try and source some more. Old RAM is problematical, because if its not standard laptop sodimms, it may not be economic to buy. 

I would be interested to know how it runs with only 64mb. How many apps can you have open at one time, etc. 

Anyway, I hope this old laptop proves useful to you again...

---

### Post by carverj on 2007-04-24
The solution seemed to be Knoppix in my situation after trying everything else! Handles multiple apps. without crashing 
:)

---

### Post by aquavitae on 2007-05-02
It runs ok, not great but usable.  Two apps running is about the limit.  I last had gentoo on it with fluxbox and it was noticably faster (i.e. Usable with kdevelop, lyx, aterm running a gcc compile and a lightweight file manager all open at once.) but gentoo is not really good on slow computers because of all the compiling required to install anything.  But this serves my purposes, which is to have something I can use when I'm away from my desktop.

---

### Post by daradib on 2007-06-15
Same problem here when trying to install Xubuntu on a friend's Pentium III computer using the alternate install CD. The CD went to low memory mode. I wiped his entire hard disk with the guided option. While proceeding through installation, the installation hangs at 65% during "Select and install software" when "Configuring anthy." Pressing Alt-F4 yields the following:

```
in-target: Setting up anthy (7900-3build1) ...
debconf : Obsolete command TITLE Configuring anthy called
in-target : Updating anthy.dic...

```

The hard disk is being constantly used therefore the computer has not frozen. Gonna leave it on overnight and see what happens.

EDIT: I left it on overnight and Xubuntu finished installing 15 hours after I started the installation.

---

### Post by Gremlinzzz on 2007-06-15
Anthy is a system for Japanese input method. It converts Hiragana text to Kana Kanji mixed text.

---

