---
title: "Upgrade from 7.10 to 8.04 not working"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by JangoJarango on 2008-05-27
Hello!

I have a problem with upgrading from ubuntu 7.10 to ubuntu 8.04 LTS.

i receive the following errors:

when trying do-release-upgrade:

```

[root@computer] # do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmpX-h3q_/hardy.tar.gz'
authenticate '/tmp/tmpX-h3q_/hardy.tar.gz' against '/tmp/tmpX-h3q_/hardy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:

gpg: WARNUNG: Unsichere Zugriffsrechte des Home-Verzeichnis `/tmp/tmpX-h3q_'

gpg: Signatur am Fre 09 Mai 2008 18:46:50 CEST mit DSA Schlüssel, ID 437D05B5, erfolgt
gpg: Unterschrift kann nicht geprüft werden: Öffentlicher Schlüssel nicht gefunden

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.

```

and when I try apt-get dist-upgrade:

```

[root@computer] # apt-get dist-upgrade
Paketlisten werden gelesen... Fertig
AbhÃ¤ngigkeitsbaum wird aufgebaut
Reading state information... Fertig
Berechne Upgrade...Fertig
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

```

also, when i try upgrading via update-manager (the GUI), it tells me that a new version 8.04 LTS is available.
when i try to update, i get the following output on the console:
```

[root@computer] # update-manager
extracting '/tmp/tmpc1475D/hardy.tar.gz'
authenticate '/tmp/tmpc1475D/hardy.tar.gz' against '/tmp/tmpc1475D/hardy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information:

gpg: WARNUNG: Unsichere Zugriffsrechte des Home-Verzeichnis `/tmp/tmpc1475D'

gpg: Signatur am Fre 09 Mai 2008 18:46:50 CEST mit DSA Schlüssel, ID 437D05B5, erfolgt
gpg: Unterschrift kann nicht geprüft werden: Öffentlicher Schlüssel nicht gefunden

```

this translates pretty much to: 
gpg:Warning: Insecure access rights of the home directory '/tmp/tmpc1475D'

and
gpg: signature cannot be checked: public key not found

the GUI Application shows the following error:

```

Echtheitsbestätigung fehlgeschlagen
Die Aktualisierungen konnten nicht auf ihre Echtheit überprüft werden. Möglicherweise gibt es Probleme mit dem Netzwerk oder dem Server

```
In english, this translates to the following:

Authenticity check failed
The Updates could not be checked for authenticity. Maybe there are Problems with the Network or the Server.


I don't understand why apt-get thinks that there is no distribution upgrade available! 


Does anyone have any idea how this can be resolved?

here is the content of my /etc/apt/sources.list:

```

[root@computer] # vim /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://at.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://at.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted


```

please help me!

thank you,
andreas

---

