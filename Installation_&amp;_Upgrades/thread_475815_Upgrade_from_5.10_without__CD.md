---
title: "Upgrade from 5.10 without  CD?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by mjhs on 2007-06-16
The situation;

* My parents' computer which was running XP recently died
* I installed an old Ubuntu (5.10) CD I had onto the computer so that it would become operational again
* I now want to upgrade to the latest version of Ubuntu, mainly so that Firefox is updated as I'm too much of a linux novice to install FF2 manually.

The problems;

* 5.10 is no longer supported, so using update manager and/or synaptic package manager doesn't work.
* The internet connection here is too slow to download the latest version, and anyway I don't have a CD to save on to here.
* I'm going away tomorrow, so I don't have time to order and wait for an install CD.
* The computer is slow enough with 5.10, and although it easily meets the requirements for 7, I'm not sure it'll be useable anyway.


Any solutions? Bear in mind I want this sorted tonight (Currently 8pm local time).

Thanks!

---

### Post by logos34 on 2007-06-16
Get the '[Minimal install' version here]("https://help.ubuntu.com/community/Installation/MinimalCD?highlight=%28Installation%29").  Choose 7.04 Feisty.  Then use a lighter, less resource-hungry desktop like Xfce (-->'xubuntu-desktop' metapackage), Fluxbox, or the like.

That's your only option as I see it.

---

### Post by logos34 on 2007-06-16
> and anyway I don't have a CD to save on to here

ok, then you could do an installation from linux.  Download the minimal install iso and use these instructions to do it from the hard drive and network:
[https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromLinux?highlight=%28installation%29)

---

### Post by mjhs on 2007-06-16
Thanks for that - that seems really good and clear advice. Unfortunately, when I went to download the minimal install package, the computer promptly died again!
Guess we're back to square one now - if I were to get hold of a Feisty install CD, how would I go about making it as non resource-hungry as possible? Sorry, I'm really an absolute Ubuntu beginner!

Thanks again.

---

### Post by logos34 on 2007-06-16
> Guess we're back to square one now - if I were to get hold of a Feisty install CD, how would I go about making it as non resource-hungry as possible? Sorry, I'm really an absolute Ubuntu beginner!

Well, in that case I would just skip ubuntu and download the Xubuntu 7.04 install disk-- specifically the text mode alternate install version [xubuntu-7.04-alternate-i386.iso ]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/")  (686MB)

Or if downloading is not an option at all, you can use the free 'ShipIt' Ubuntu Feisty CD (alas there is no Xubuntu shipit cd) and just install [Xubuntu from Ubuntu]("http://www.xubuntu.org/get") using the xubuntu-desktop package as I mentione above.  Then just logon to that desktop each session (and maybe even delete the ubuntu gnome desktop altogether.

---

### Post by Pumalite on 2007-06-16
> **logos34 said:**
> Well, in that case I would just skip ubuntu and download the Xubuntu 7.04 install disk-- specifically the text mode alternate install version [xubuntu-7.04-alternate-i386.iso ]("http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/")  (686MB)

Or if downloading is not an option at all, you can use the free 'ShipIt' Ubuntu Feisty CD (alas there is no Xubuntu shipit cd) and just install [Xubuntu from Ubuntu]("http://www.xubuntu.org/get") using the xubuntu-desktop package as I mentione above.  Then just logon to that desktop each session (and maybe even delete the ubuntu gnome desktop altogether.

If you continue to have problems, you could give this a try:

[http://zenwalk.org/](http://zenwalk.org/)

---

