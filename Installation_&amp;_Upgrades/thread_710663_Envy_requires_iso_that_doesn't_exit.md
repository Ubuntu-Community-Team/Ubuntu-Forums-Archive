---
title: "Envy requires iso that doesn't exit"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by xen-uno on 2008-02-28
edit: exit = exist

Trying to run latest Envy legacy build so that I can get off this 800 x 600 vesa mode I've been stuck on forever. Using a BFG (NVidia) 8800GT. Envy runs fine up until a point and then asks for the "Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)" CD ... I did not use that version to install (I used "ubuntu-7.10-alternate-amd64"). I can't even find that iso version on the net. Application>Add/Remove>NVidia binary X.Org driver ('new' driver) is asking for the same CD now. I've had to use so many bits and pieces of so many threads and "how-to's" in several vain attempts that I'm thoroughly confused now. Any ideas?

---

### Post by taurus on 2008-02-28
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by xen-uno on 2008-02-29
OK ... that's where it's coming from (thank you) ... what can I do about it? I'll try the Live (non-alternate) x64 CD and see what happens (seems like I've tried before ... same result).

```
jan@planet64x:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted

[color=blue]deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted[/color]
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

edit: I might have a clue. Exploring the alt CD I see a README.DISKDEFINES in the root. First line item in the file is ...
#define DISKNAME  Ubuntu 7.10 "Gutsy Gibbon" - Release amd64

If I replace the erroneous string between the brackets in the blue line of the code window and insert the one above ... it should work? Looks like I'll have to do it as user ROOT, as it complains I don't have permission to do it as JAN.

---

### Post by soulskater on 2008-02-29
Hi.

Do you have internet connection to your PC?

If you do, go to System/Administration/Software Sources and 
deselect the CD as a source for software source.

Now it should fetch everything from the internet and disregard the CD.

/soulskater

---

### Post by xen-uno on 2008-02-29
Yes I do ... I'll try that ... thanks!!!

---

