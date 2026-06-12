---
title: "List of Repos for Jaunty"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by falkTX on 2009-04-09
I'm trying to find some good Jaunty repositories before the real deal comes out.

Here's my sources.list

```
## Main Repos
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse

## Source Repos
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security restricted main multiverse universe

## Outro
deb http://archive.canonical.com/ubuntu jaunty partner #Partner
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://dl.google.com/linux/deb/ stable non-free #Google
deb http://packages.medibuntu.org/ jaunty free non-free #Medibuntu
deb http://wine.budgetdedicated.com/apt jaunty main #Wine

## PPAs
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #Chromimum-Daily
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main #GlobalMenu-Team
deb http://ppa.launchpad.net/rvm/ppa/ubuntu jaunty main #(S)Mplayer
deb http://ppa.launchpad.net/samrog131/ppa/ubuntu jaunty main #Samrog131 (Small KDE Stuff)
deb http://ppa.launchpad.net/tobydox/ppa/ubuntu jaunty main #TobyDox (LMMS/MingX)
deb http://ppa.launchpad.net/tonio/ppa/ubuntu jaunty main #Tonio (Cool KDE Stuff)
deb http://ppa.launchpad.net/ubuntustudio-dev/ppa/ubuntu jaunty main #UbuntuStudio.Devel
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main #Tulatrix (Ubuntu-Tweak)
```

The Partner is the official Ubuntu partner repo. Then I have Opera (official), Google, Medibuntu and the latest Wine (doesn't include winegecko-0.9.1 right now).

For the PPAs, I have the Linux port of Google Chrome (alpha!), the globalmenu-team (if you don't know what it is, leave it), updated mplayer/mencoder/smplayer/codecs from the official devs, samrog131 that has some extra KDE stuff from kde-apps.org, the official LMMS repo (doesn't have any packages, yet), Tonio that has some SVN updated KDE stuff (including k3b-kde4!!), the UbuntuStudio, and Ubuntu-Tweak.


I'm still looking for the Cairo-Dock debian repo, and any more repos that are good & stable.

If you know any, please tell me

---

### Post by go7Ul1ai on 2009-04-09
Try installing Ubuntu-Tweak ([http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)), there is a list of great third-party sources there :)

---

### Post by falkTX on 2009-04-09
> **lee.jarratt said:**
> Try installing Ubuntu-Tweak ([http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)), there is a list of great third-party sources there :)

Some of my repos are taken from there. But most of the ubuntu-tweak repos are unstable/pre-release stuff, so I don't use them

---

### Post by go7Ul1ai on 2009-04-09
> **falkTX said:**
> Some of my repos are taken from there. But most of the ubuntu-tweak repos are unstable/pre-release stuff, so I don't use them

Okay, I guess you won't be interested in the Ubuntu Tweak Development repos then? ^_^

---

### Post by fabounet on 2009-04-09
there will be a Debian repos for Cairo-Dock2 :-)

---

### Post by DizzyTech on 2009-04-09
That looks to be just about every repo that's both useful and available on Jaunty.  :lolflag:

---

