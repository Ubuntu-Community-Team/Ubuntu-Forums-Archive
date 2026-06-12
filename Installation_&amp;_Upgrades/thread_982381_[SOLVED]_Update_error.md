---
title: "[SOLVED] Update error"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by PeregrinGo on 2008-11-14
Hello everyone,

I keep getting the same error in Update Manager everytime I attempt to "check" or confirm the status of available updates. My OS is installed in Spanish, so I'm not certain exactly what the English equivalents are called. At any rate, the update manager states it has not been updated in 25 days. (Even though it sometimes automatically detects individual upgrades / updates which I am able to install.) 

When running the update check, the system always gets to 57 of 58 files / updates, and then, after a moment or so, it gives me the following error:

```
W: Imposible obtener (Impossible to obtain) http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg  No pude conectarme a (Unable to connect to) akirad.hfbk.net:80 (193.174.241.68), expiró tiempo para conexión

W: Imposible obtener (Unable to obtain / get) http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-es.bz2  No pude conectarme a akirad.hfbk.net http:

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar. (Some index files weren't able to be downloaded, they have been ignored, or older files have been used in their place.)

```

I really would appreciate any help you can provide. By the way, I am using Hardy.

---

### Post by PeregrinGo on 2008-11-14
Hello everyone, not sure which forum this should go into, so I posted it in the general category first.

I keep getting the same error in Update Manager everytime I attempt to "check" or confirm the status of available updates. My OS is installed in Spanish, so I'm not certain exactly what the English equivalents are called. At any rate, the update manager states it has not been updated in 25 days. (Even though it sometimes automatically detects individual upgrades / updates which I am able to install.) 

When running the update check, the system always gets to 57 of 58 files / updates, and then, after a moment or so, it gives me the following error:

> W: Imposible obtener (Impossible to obtain) [http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg](http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg)  No pude conectarme a (Unable to connect to) akirad.hfbk.net:80 (193.174.241.68), expiró tiempo para conexión (the connection timed out)

W: Imposible obtener (Unable to obtain / get) [http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-es.bz2](http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-es.bz2)  No pude conectarme a (Unable to connect to) akirad.hfbk.net http:

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar. (Some index files weren't able to be downloaded, they have been ignored, or older files have been used in their place.)


I really would appreciate any help you can provide. By the way, I am using Hardy.

---

### Post by bapoumba on 2008-11-14
Threads merged.
I cannot get to these either. Please post the output of:
```
cat /etc/apt/sources.list
```
Or disable the repos giving you trouble if you know how to do it. Then run the update again (or reload button from synaptic).

---

### Post by Steve1961 on 2008-11-14
If you still get the error after manually running sudo apt-get update from a terminal try changing the download mirror in system/administration/software sources

---

### Post by PeregrinGo on 2008-11-15
> **bapoumba said:**
> Threads merged.
I cannot get to these either. Please post the output of:
```
cat /etc/apt/sources.list
```
Or disable the repos giving you trouble if you know how to do it. Then run the update again (or reload button from synaptic).

Sorry for the double-posting. I wasn't sure if "updates" counted as upgrades, and thus, I decided to try both here and the General forum. =o)

I ran "cat /etc/apt/sources.list" and got the following:

> ## deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main


---

### Post by PeregrinGo on 2008-11-15
> **Steve1961 said:**
> If you still get the error after manually running sudo apt-get update from a terminal try changing the download mirror in system/administration/software sources

I just ran that manual update in the terminal, and it gave me the same problem. So then I changed mirrors as you suggested. But this didn't fix the problem either. 

I looked up that repository and found that it was used principally for Cinelerra, and since I am no longer using that program (I downloaded Kino), I disabled those repositories then deleted the akirad-related files.

Update worked fine. Thanks for your help. Not sure what's wrong with those repositories, but at least they're ones I don't need!

---

### Post by bapoumba on 2008-11-15
I'm sorry, but I do not see where that "akirad.hfbk.net" reference is coming from. This is the one giving you trouble. I browsed the Dell PPA packages, and they do not mention it.

Do you have any other repos?

Please post the output of:
```
sudo apt-get update
```

Edit, I see you solved this as I was posting. Congrats!

---

### Post by PeregrinGo on 2008-11-15
> **bapoumba said:**
> 
Edit, I see you solved this as I was posting. Congrats!


No. Thank you. I wouldn't have known to disable that repository if not for your post. Cheers.

---

