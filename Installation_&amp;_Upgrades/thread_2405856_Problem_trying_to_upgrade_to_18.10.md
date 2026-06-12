---
title: "Problem trying to upgrade to 18.10"
date: 2018-11-12
forum: Installation &amp; Upgrades
---

### Post by kari0ca on 2018-11-12
Hi there, i've been trying to upgrade to 18.10 from 18.04 with no sucess, i'm using kubuntu.


when i try to upgrade, i get this message:
```
Os pacotes a seguir serão mantidos em suas versões atuais: (wich means: The following packages will be kept in their current versions:)
gconf-service libfile-fcntllock-perl libgconf-2-4 liblocale-gettext-perl libnet-dbus-perl libnih1 libtext-iconv-perl libxml-parser-perl
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 8 não atualizados. (0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded)

```


I've tried: ```
dpkg --configure -a
``` and ```
sudo apt-get -f install
``` but no success, even tried to install the package that is in the list: ```
apt list --upgradable
```
this list of upgradable packages returns:
```
gconf-service/stable 3.2.6-4+b1 amd64 [upgradable from: 3.2.6-4ubuntu1]
libfile-fcntllock-perl/stable 0.22-3+b2 amd64 [upgradable from: 0.22-3build2]
libgconf-2-4/stable 3.2.6-4+b1 amd64 [upgradable from: 3.2.6-4ubuntu1]
liblocale-gettext-perl/stable 1.07-3+b1 amd64 [upgradable from: 1.07-3build2]
libnet-dbus-perl/stable 1.1.0-4+b1 amd64 [upgradable from: 1.1.0-4build2]
libnih1/stable 1.0.3-8 amd64 [upgradable from: 1.0.3-6ubuntu2]
libtext-iconv-perl/stable 1.7-5+b4 amd64 [upgradable from: 1.7-5build6]
libxml-parser-perl/stable 2.44-2+b1 amd64 [upgradable from: 2.44-2build3]
```
Does anyone knows how can i upgrade these packages?


Thanks in advance

---

### Post by 23dornot23d on 2018-11-12
I use aptitude ....... you could try it ......... as answering no to its first choice may give you another that is better ....... so far I have had good success with it.

I usually try to choose where it does not want to start removing packages that I know I will need ....... that is the only part you may have problems with
but post back once you get a result from it that looks ok ......... or as always - wait for a better answer to your problem.

**sudo apt-get install aptitude**

will load it up

**sudo aptitude update**

[B]sudo aptitude safe-upgrade

[/B]See how it goes for listing the problems ......... if any ........ or answer no to the first set of installable items and see what it gives you next.

---

### Post by kari0ca on 2019-01-20
> **23dornot23d said:**
> I use aptitude ....... you could try it ......... as answering no to its first choice may give you another that is better ....... so far I have had good success with it.

I usually try to choose where it does not want to start removing packages that I know I will need ....... that is the only part you may have problems with
but post back once you get a result from it that looks ok ......... or as always - wait for a better answer to your problem.

**sudo apt-get install aptitude**

will load it up

**sudo aptitude update**

[B]sudo aptitude safe-upgrade

[/B]See how it goes for listing the problems ......... if any ........ or answer no to the first set of installable items and see what it gives you next.

Hi 23dornot23d,

the result of the commands were the follwing:

```

Solving dependencies ...
To that end, updated or removed.
0 packages upgraded, 0 new installed, 0 removed and 9 not upgraded.
You must get 0 B of files. After unpacking, 0 B will be used.

```

---

### Post by oldos2er on 2019-01-20
Try ```
sudo apt update && sudo apt full-upgrade
``` If there any errors please post the entire command and all its output.

If there are no errors you can continue with ```
do-release-upgrade
``` I'm assuming you've set Software & Updates to show possible upgrades to "any new version" rather than "for long term support versions."

---

