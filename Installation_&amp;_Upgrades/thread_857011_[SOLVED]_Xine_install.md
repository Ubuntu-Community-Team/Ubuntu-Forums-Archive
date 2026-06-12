---
title: "[SOLVED] Xine install"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by stolzi on 2008-07-12
Hello,

i am not new to linux, but to ubuntu... I have problems to install xine in xubuntu 8.04 

```
~$ sudo aptitude install xine-ui libxine-extracodecs
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Initialisiere Paketstatus... Fertig
Schreibe erweiterte Statusinformationen... Fertig
Erzeuge Tag-Datenbank... Fertig                  
Konnte kein Paket finden, dessen Name oder Beschreibung auf »xine-ui« passt.
Konnte kein Paket finden, dessen Name oder Beschreibung auf »libxine-extracodecs« passt.

```

He didnt find the packages. I tried to find an answer in google. But what i found was that i have to activate package source universe... But it is already activated and the packages couldnt be found at all.

Can you help me?

Thanks
Stolzi

---

### Post by iaculallad on 2008-07-12
> **stolzi said:**
> Hello,

i am not new to linux, but to ubuntu... I have problems to install xine in xubuntu 8.04 

```
~$ sudo aptitude install xine-ui libxine-extracodecs
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Initialisiere Paketstatus... Fertig
Schreibe erweiterte Statusinformationen... Fertig
Erzeuge Tag-Datenbank... Fertig                  
Konnte kein Paket finden, dessen Name oder Beschreibung auf »xine-ui« passt.
Konnte kein Paket finden, dessen Name oder Beschreibung auf »libxine-extracodecs« passt.

```

He didnt find the packages. I tried to find an answer in google. But what i found was that i have to activate package source universe... But it is already activated and the packages couldnt be found at all.

Can you help me?

Thanks
Stolzi

Why install it, Isn't xine pre-installed in Xubuntu?

EDIT: Maybe, you should be doing this:

Add Medibuntu restricted Repository and download the codec packs:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install vlc libdvdcss2 ubuntu-restricted-extras w32codecs

```

And add the totem-xine player:

```
sudo apt-get install totem-xine
sudo update-alternatives --config totem

```

---

### Post by lisati on 2008-07-12
If the translation from [http://freetranslation.com]("http://freetranslation.com/") is any guide, I think the error messages are saying that it is unable to find libxine extracodecs or xine ui

Try using the Add/Remove programs menu to add the Gstreamer plugins. I'm not sure what that's called in German.....

---

### Post by stolzi on 2008-07-12
Yes, he says, that he cant find this packages. For what reason should i install gstreamer? I only want to install xine-ui.

@iaculallad
No, xine-ui is not installed, only totem is allready installed, but i need xine-ui for special reason. So i think your manual is not useful for installing xine-ui?

So, can anyone tell me how i get xine-ui? :confused:

:) Thanks

---

### Post by Partyboi2 on 2008-07-12
can you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by stolzi on 2008-07-12
Sicher: ```
#deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by Partyboi2 on 2008-07-12
Your sources.list seems fine. You could try downloading the xine-ui package manually and installing it from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=xine-ui&searchon=names&suite=all&section=all")[FONT=monospace]
[/FONT]libxine-extracodecs package is not available for hardy

---

### Post by stolzi on 2008-07-12
But i would be interested in the reason why it is not working... Doesnt anyone know?

---

### Post by Partyboi2 on 2008-07-12
I just tried using ```
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
``` and got the same message as you were getting. But by changing  download server to "main" under Software Sources fixed it.
So the package must be missing from the de universe repo

---

### Post by stolzi on 2008-07-12
Can you help me understand this? If i have read right, then universe is only an extension of main and not a replacement? If this is right i dont understand why there are only universe sources in my sources.list by default?

Can, or should i _add_ main to my universe, or is better to get only this package from main and then let the old setting with universe? If i should add... how should it look like in my sources.list?

Thanks
Stozi

---

### Post by Partyboi2 on 2008-07-12
> If i have read right, then universe is only an extension of main and not a replacement? If this is right i dont understand why there are only universe sources in my sources.list by default?
There are 4 components that make up the ubuntu repositories they are Main, Restricted, Universe and  Multiverse. It is recommend to have them enabled under Software Sources. You can read more about it from [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu")
Your current sources.list shows that you have them all enabled.

---

### Post by stolzi on 2008-07-15
Hmm strange. Now it worked without activating any more and i found all xine packages. Like you said allready all sources were activated... Perhaps he had to update the database first.
Thanks for help

---

