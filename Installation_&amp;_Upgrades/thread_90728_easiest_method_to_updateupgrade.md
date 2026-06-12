---
title: "easiest method to update/upgrade"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by missmoondog on 2005-11-15
i've been browsing around here most of the afternoon checking out all the articles on updating/upgrading. sure seems to be quite a few different ways.

i have converted 2 of my machines over to strictly ubuntu 5.04 and 2 of them dual booting xp/5.04 and 1 dual booting xp/5.10. was a totally clean machine that didn't already have 5.04 on it.

what's the EASIEST way for this first time upgrader to make the transition without losing stuff on those other 2 computers?

thank you

---

### Post by Kyral on 2005-11-15
Transition to 5.10?

Crack open your /etc/apt/sources.list and replace every instance of hoary with breezy. Then save and....

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by missmoondog on 2005-11-16
yes, transition/upgrade to 5.10.
that's the way it seems most of the topics i've come across have said to do it, but what i'm concerned about is some of the articles i've found have mentioned removing a bunch of stuff related to dependency issues, or something like that?

---

### Post by doclivingston on 2005-11-16
If you have .debs installed, either from other repositories or downloaded, then they can cause problems. It's also a good idea to ensure that the "ubuntu-desktop" (or kubuntu-desktop) package is installed, you may have removed it if you uninstalled any default packages.

---

### Post by missmoondog on 2005-11-16
thanks doc.
i should be ok there.

i'm about to try this on a machine that just has ubuntu on it so i'm not real worried if something doesn't go quite right. i'm hoping i can do this the same way on my dual boot machines and it's not going to mess with windows, correct?

Hmm! took 9 minutes to run into a snag. first time i've seen this now.
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
You may want to run apt-get update to correct these problems
that what brought up that error to begin with - sudo apt-get update
how do i fix that?

---

### Post by frodon on 2005-11-16
All is describe here, it worked really well for me and most of people here : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29)

---

### Post by Biased turkey on 2005-11-16
[QUOTE=frodon]All is describe here, it worked really well for me and most of people here : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29)[/QUOTE]


Is ubuntu-desktop installed by default on a "norma user model" ( not expert mode ) installation ?

---

### Post by frodon on 2005-11-16
yes, but you need to reinstall it before the upgrade to avoid some problems.

---

### Post by missmoondog on 2005-11-16
well that surely didn't go smooth for me. i reinstalled the desktop just to make sure before i started the upgrade. got all kinds of errors about something and then it said falling back to something. don't remember the wording exactly, as i did the upgrade this morning and it's now almost midnight. what it boiled down to is i wound up with no desktop anyway. just as well. re-installed xp pro and ubuntu 5.10 from scratch. didn't really want to put windows back on this machine, but ubuntu/linux just doesn't cut the mustard for my needs for certain apps that i use regularily.

---

