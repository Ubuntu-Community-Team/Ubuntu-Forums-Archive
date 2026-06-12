---
title: "My /etc/apt/sources.list dirty?"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by badp on 2008-04-02
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to <snip>

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the <snip>
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu <snip>
deb http://archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu <snip>
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports' <snip>
deb http://it.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu gutsy/
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe
```

Is it me or there's something wrong with the bottom of the file? I think I see duplicates and leftovers from Feisty. I added the Miro repository myself.

PS: <snip>'s are my addition for readers' convenience.

---

### Post by Pumalite on 2008-04-02
If you are running Gutsy, get rid of the Feisty lines by putting a # in front of it.

---

### Post by aysiu on 2008-04-02
Yes, you should [get a clean list.](http://www.psychocats.net/ubuntu/sources#key)

---

### Post by badp on 2008-04-04
Now repository updates are faster (duh!). Thank you.

---

