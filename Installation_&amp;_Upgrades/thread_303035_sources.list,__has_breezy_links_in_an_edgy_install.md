---
title: "sources.list,  has breezy links in an edgy installation"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by tinker123 on 2006-11-19
I am running the latest greatest, Ubuntu 6.10, edgy..from an upgrade.

I peaked in /etc/apt/sources.list and I see "breezy" in most of the urls.   Is this normal?

I ask because I ran an old copy of automatix ( that I installed back when my system was in breezy ) and I am wondering if it changed/set back my sources.list

---

### Post by Jussi Kukkonen on 2006-11-19
If the references to breezy are on lines that start with a "#", then they're just comments. If they are on normal lines, you are quite close to trashing your installation: do not do any upgrading or installing before you've fixed it!

---

### Post by tinker123 on 2006-11-19
Nope, the "breezy" references are not in comments, they are in the URL, oddly, with white space between the preceeding "/" and them.

How do I fix this problem?

---

### Post by arnieboy on 2006-11-19
> **tinker123 said:**
> Nope, the "breezy" references are not in comments, they are in the URL, oddly, with white space between the preceeding "/" and them.

How do I fix this problem?

automatix did not upgrade your breezy installation to edgy (you did). You should have made sure all breezy repos were either deleted or commented before you actually went for the upgrade.
Why dont you paste the result of the following command?
```
cat /etc/apt/sources.list
```

---

### Post by Jussi Kukkonen on 2006-11-19
He never claimed Automatix did that. He was suggesting that running a Breezy-era-Automatix possibly added/changed some Breezy-lines into his sources.list. Are you saying that is not possible?

---

### Post by arnieboy on 2006-11-19
> **Jussi Kukkonen said:**
> He never claimed Automatix did that. He was suggesting that running a Breezy-era-Automatix possibly added/changed some Breezy-lines into his sources.list. Are you saying that is not possible?
thats only possible if the version of automatix he used was one of the first versions released (more than an year back when distro checking had not been introduced).
My apologies for misunderstanding the question.

---

### Post by tinker123 on 2006-11-19
> **arnieboy said:**
> thats only possible if the version of automatix he used was one of the first versions released (more than an year back when distro checking had not been introduced).
My apologies for misunderstanding the question.

I think that is the case.  I started with Breezy a long time back, got an early copy of automatix and I always assumed it would just get new stuff.

---

### Post by tinker123 on 2006-11-19
> **arnieboy said:**
> thats only possible if the version of automatix he used was one of the first versions released (more than an year back when distro checking had not been introduced).
My apologies for misunderstanding the question.

> **arnieboy said:**
> automatix did not upgrade your breezy installation to edgy (you did). You should have made sure all breezy repos were either deleted or commented before you actually went for the upgrade.
Why dont you paste the result of the following command?
```
cat /etc/apt/sources.list
```


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

---

### Post by arnieboy on 2006-11-19
yes thats a breezy sources.list
Please restore the backup which automatix must have made in your /etc/apt folder (it will have date and time tags at the end)
and then do a 
```
sudo apt-get update
```

---

### Post by tinker123 on 2006-11-21
I checked the backups to sources.list.   For some reason, I have no idea why, they all say "breezy".

Is there anywhere I can get a basic sources.list for edgy to start over?

Would replacing all instances of "breezy" with "edgy" work?

---

### Post by tinker123 on 2006-11-23
I pulled an edgy sources.list off of the net, got a quick education about gpg keys, did an apt-get update and then an apt-get dist-upgrade.  All seems to be well now.

---

