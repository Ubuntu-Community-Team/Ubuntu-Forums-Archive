---
title: "[SOLVED] i cant use sudo apt-get"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by leo3307 on 2008-09-30
i can`t use sudo apt-get 
it trow me this and i have internet conection
user@pc-desktop:~$ sudo apt-get update
[sudo] password for user: 
Err [url] http://cr.archive.ubuntu.com [/ url] hardy Release.gpg
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy / main Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy / restricted Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy / universe Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy / multiverse Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-updates Release.gpg
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-updates/main Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-updates/restricted Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-updates/universe Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-updates/multiverse Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-security Release.gpg
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-security/main Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-security/restricted Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-security/universe Translation-es
   I could not resolve ': @'
Err [url] http://cr.archive.ubuntu.com [/ url] hardy-security/multiverse Translation-es
   I could not resolve ': @'
Err [url] http://archive.ubuntu.com [/ url] hardy Release.gpg
   I could not resolve ': @'
Reading package list ... Made
W: Unable to get [url] http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Unable to get [url] http://cr.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2 [/ url] Could not resolve ': @'

W: Some index files have not been able to download, have been ignored,
or has been used in some ancient place.
W: You may want to run 'apt-get update' to correct these problems

---

### Post by lukjad on 2008-09-30
Is it possible to get a translation of:
> 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
No pude resolver ':@'
Leyendo lista de paquetes... Hecho
W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

The best I can guess is that it is saying that it cannot connect to the repositories. Am I right?

---

### Post by leo3307 on 2008-09-30
this is the translation:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
I could not resolve ': @'
Reading package list ... Made
W: Some index files have not been able to download, have been ignored,
or has been used in some ancient place.
W: You may want to run 'apt-get update' to correct these problems
 
but the strange is this simbol [SIZE="5"]**:@**[/SIZE] that appears and also i can`t use the synaptic or the add and remove it says errors too:confused:

---

### Post by zvacet on 2008-09-30
```
cat /etc/apt/sources.list
```

Post it here.Does **sudo** work?You can try it by typing sudo in terminal and see the output.

---

### Post by leo3307 on 2008-09-30
> **zvacet said:**
> ```
cat /etc/apt/sources.list
```

Post it here.Does **sudo** work?You can try it by typing sudo in terminal and see the output.

yes sudo works and this is the output:
[SIZE="1"]sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://cr.archive.ubuntu.com/ubuntu/](http://cr.archive.ubuntu.com/ubuntu/) hardy-security multiverse
[/SIZE]

---

### Post by oldos2er on 2008-09-30
Are you able to access the internet?

---

### Post by leo3307 on 2008-09-30
actually i using that computers internet right now

---

### Post by oldos2er on 2008-09-30
Ok. Go to System, Administration, Software Sources, and try changing to a different server.

---

### Post by leo3307 on 2008-09-30
i already try it ut it doesn`t work

---

### Post by oldos2er on 2008-09-30
Seems an odd problem...it could be with your GPG keys. I'm not in Ubuntu right now, but check Software Sources again and see if there's a way you can reload these keys.

---

### Post by lukjad on 2008-10-01
Are you on a network or do you have direct Internet access?

---

### Post by leo3307 on 2008-10-01
i have a direct internet conection

---

### Post by leo3307 on 2008-10-01
i see that there were no a easy solution soo i create a new user and it start working perfectly so i guess it was a virus but thanks a lot:D :D
:D

---

### Post by lukjad on 2008-10-02
Sorry for not responding sooner, I came down with the bug that's doing the rounds at my school.

I doubt it was a virus, but probably it was just something that was misconfigured. Still, I'm glad your problem is fixed. :) 

See you around.

---

