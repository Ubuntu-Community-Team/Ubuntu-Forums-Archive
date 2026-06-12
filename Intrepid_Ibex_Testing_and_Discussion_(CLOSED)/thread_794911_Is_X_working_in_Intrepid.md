---
title: "Is X working in Intrepid?"
date: 2008-05-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-05-15
Hi,

Quick question: is X working on Intrepid right now? I have a spare partition for it (with its own /home) so I don't really mind it being enormously broken.

I'm just bored with a stable release, I think. I need some breakage.

---

### Post by Awalton on 2008-05-15
"Working" yes ;).

There's a bug in libxfont1 which mysteriously stops X from loading for some people (%*$@#*#$!!#), and it's a known issue, so you'll want to put a hold on it before moving to Intrepid. Otherwise it works just fine.

---

### Post by Bou on 2008-05-15
I might just not update that package, then :)

Could someone please post your Intrepid sources.list? I seem to be having some trouble with mine (as in:they won't load).

---

### Post by BradwJensen on 2008-05-15
lol excuse my lack of knowledge, but what is X?

I read people talking about "X" all the time but I never really understood what it was, or if was anything specifically.

Thanks.

---

### Post by Bou on 2008-05-15
Basically, the graphics. Seeing windows and a pointer instead of white letters on a black background.

---

### Post by ghindo on 2008-05-15
Specifically, it refers to the [X Window System](http://en.wikipedia.org/wiki/X_window_system), if you wanna look into it further.

---

### Post by caryb on 2008-05-15
X is going great the lib file was updated this morning (12 hours ago):guitar:


Cary

---

### Post by tighem on 2008-05-15
I did a fresh install of hardy in VirtualBox last night and then changed the word hardy to intrepid in the sources.list file. X is working for me, including VB guest extensions.

---

### Post by cecilpierce on 2008-05-15
Has anybody have held back packages gcc 4.2 and gpp 4.2 ?
It seems like its been like that from the begining for me, or am I doing something wrong ? Thanks, Cecil

---

### Post by nhandler on 2008-05-15
> **cecilpierce said:**
> Has anybody have held back packages gcc 4.2 and gpp 4.2 ?
It seems like its been like that from the begining for me, or am I doing something wrong ? Thanks, Cecil

I've had gcc 4.2 held back for a while as well.

@Bou, here is my Ubuntu Intrepid sources.list
> # deb cdrom:[Ubuntu 8.04 _Intrepid Ibex_ - Release i386 (20080423)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security main restricted
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security main restricted
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security universe
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security universe
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security multiverse
deb-src [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) intrepid-security multiverse

As for X, it stopped working for me about a week ago. I just did an upgrade a few hours ago, and that fixed it. So, as of now, X is working fine.

---

### Post by KIAaze on 2008-05-17
Yes, libxfont1 working for me too now. :)
Thanks for telling us about it.

As for held back packages, I currently have:
  cpp-4.2 doc-central dwww gcc-4.2-base libgfortran2

---

### Post by spamzilla on 2008-05-19
Guess what I'm doing when I get home from work :D

---

### Post by LaRoza on 2008-05-19
I am in Intrepid now. Just upgrading all the packages again. Hopefully, X will work. (It isn't at the moment, using lynx).

---

### Post by LaRoza on 2008-05-19
X works now :-)

---

### Post by zorkerz on 2008-05-29
Is the best way to get intrepid to upgrade from a hardy install (say sudo update-manager -d) or to replace hardy with intrepid in sources.list? Is there any other way?

---

### Post by spamzilla on 2008-05-30
> **zorkerz said:**
> or to replace hardy with intrepid in sources.list? Is there any other way?

Do that

---

