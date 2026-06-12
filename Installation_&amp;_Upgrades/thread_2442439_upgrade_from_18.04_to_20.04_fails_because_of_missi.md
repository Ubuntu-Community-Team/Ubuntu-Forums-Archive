---
title: "upgrade from 18.04 to 20.04 fails because of missing"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by jaives on 2020-05-03
[FONT=Arial]Message:
"
lFout tijdens het bijwerken [/FONT]

[FONT=Arial]Tijdens de update heeft zich een probleem voorgedaan. De oorzaak et [/FONT]
[FONT=Arial]hiervan is meestal een netwerkprobleem. Gelieve uw netwerkverbinding [/FONT]
[FONT=Arial]te controleren en probeer het dan opnieuw. [/FONT]

[FONT=Arial]W:Bijwerken van de pakketlijst uit een dergelijke pakketbron kan niet [/FONT]
[FONT=Arial]veilig gebeuren en is daarom standaard uitgezet., W:Zie de man-pagina [/FONT]
[FONT=Arial]apt-secure(8) voor details over het aanmaken van een pakketbron en [/FONT]
[FONT=Arial]over de configuratie langs gebruikerskant., E:De pakketbron [/FONT]
[FONT=Arial]'[/FONT][http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu)[FONT=Arial] zesty-updates Release' heeft [/FONT]
[FONT=Arial]geen Release-bestand., W:Bijwerken van de pakketlijst uit een [/FONT]
[FONT=Arial]dergelijke pakketbron kan niet veilig gebeuren en is daarom standaard [/FONT]
[FONT=Arial]uitgezet., W:Zie de man-pagina apt-secure(8) voor details over het [/FONT]
[FONT=Arial]aanmaken van een pakketbron en over de configuratie langs [/FONT]
[FONT=Arial]gebruikerskant., E:De pakketbron '[/FONT][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)
[FONT=Arial]zesty-security Release' heeft geen Release-bestand.
"
aparantly a packet source 'zesty' has no 'release-file'

How can I solve this?
I am a novice in Ubuntu and Linux, so I look for a very easy and clear way to get out of this situation.
If there is not such a solution, I will try to unistall 18.04 and start a new installation from scratch.[/FONT]

---

### Post by CelticWarrior on 2020-05-03
Welcome.

Indeed, a fresh installation is faster and often better than an upgrade.
That said, the mention of "zesty" points to Ubuntu 17.04 which is very different than 18.04 LTS. "zesty" is out off support since January 2018 and shouldn't be used and either way couldn't upgrade directly to 20.04; it would have to follow the route 17.04>17.10>18.04 at which point it could be upgraded to 20.04 LTS. "bionic" (18.04) is a LTS release supported until April 2023 and can, as explained before, be upgraded directly to the next LTS which is 20.04.

PS - except in the LoCo subsection this forum is English only. When your post requires showing terminal output please always start the session with "LANG=C" in order to have the output in plain English.

---

### Post by Impavidus on 2020-05-04
Goeiemorgen (I'll continue in english so that our friend from Galiza can follow us too).

Your problem is indeed an old repository for Ubuntu 17.04. If this is just one stray repository in a list that otherwise uses bionic (which is 18.04), you can disable it, either via the menu or by directly modifying the configuration file. It is /etc/apt/sources.list or, if using an unofficial source, one of the files in /etc/apt/sources.list.d. If all your repositories refer to zesty instead of bionic, you run Ubuntu 17.04, not 18.04. If in doubt, show us the complete contents of your /etc/apt/sources.list.

The upgrade path from 18.04 to 20.04 hasn't been officially opened yet. That will happen after the release of 20.04.1, probably in late July or early August. You can upgrade before that, but keep in mind that the upgrade process hasn't been properly tested. Ubuntu 17.04 is dead. There's no sensible way to upgrade it.

---

### Post by jaives on 2020-05-05
First of all, I want to thank you for looking at my problem.

Please find hereafter the content of the  etc/apt/sources.list
'
```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) zesty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic universe
deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-updates universe
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) zesty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic multiverse
deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-updates multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) zesty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) zesty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner


deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security main restricted
deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security universe
deb [http://ftp.belnet.be/ubuntu.com/ubuntu/](http://ftp.belnet.be/ubuntu.com/ubuntu/) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security multiverse
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) bionic main universe restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main universe restricted
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) bionic-updates main universe restricted
deb [http://ftp.tudelft.nl/archive.ubuntu.com/](http://ftp.tudelft.nl/archive.ubuntu.com/) bionic-backports main universe restricted
```
'
I am not allowed to do any changes to the sources.list file (I can make modifications with the notepad, but I cannot save the file to sources.list (I am only allowed to save to a file with another filename; I could then change the name, but I fear to end up with a system not running any longer)

---

### Post by Impavidus on 2020-05-06
Your sources.list is messy, but all the important sources for 18.04 are there, so you should have a decent 18.04 system. You use two different servers for upgrades (in addition to the main server for security upgrades), one in Belgium, one in the Netherlands. To clean it up, make it look somewhat like this. I'll use the Belgian server as most of your sources use that.```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.
deb http://ftp.belnet.be/ubuntu.com/ubuntu main restricted
# deb-src http://ftp.belnet.be/ubuntu.com/ubuntu main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.belnet.be/ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://be.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.belnet.be/ubuntu.com/ubuntu/ bionic universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ bionic universe
deb http://ftp.belnet.be/ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://be.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.belnet.be/ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://ftp.belnet.be/ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.belnet.be/ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://be.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

## Security updates.
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```
First make a backup of your messy sources.list (because it's still better than nothing, in case you completely mess up), then edit the file to look like above. Use the sudoedit command to edit the file. Type your password followed by enter. Then it will use the nano text editor to edit the file (unless you configured it otherwise). Use ctrl-o to save ctrl-x to quit.```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudoedit /etc/apt/sources.list
```

---

