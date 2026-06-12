---
title: "continue using 16.04 after EOL - change of repository in sources.list"
date: 2022-05-30
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2022-05-30
I'd like to continue using my old 32 bit laptop with ubuntu-mate 16.04 and install corresponding versions of programs e.g. like gnuplot-x11. According to [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) I only need to change the sources.list accordingly. However, when running an update I get a list of error messages indicating that the repositories were not found (see below). My sources.list look like in the above link with "CODENAME" replaced with "xenial".
Thanks for hints as to what might be wrong!

Ign:4 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial-updates InRelease           
Ign:5 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial-security InRelease          
OK:6 [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) xenial InRelease         
Ign:7 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial-backports InRelease       
Fehl:8 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial Release
  404  Not Found [IP: 185.125.190.40 80]
Fehl:9 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial-updates Release
  404  Not Found [IP: 185.125.190.40 80]
Fehl:10 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial-security Release
  404  Not Found [IP: 185.125.190.40 80]
Fehl:11 [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial-backports Release
  404  Not Found [IP: 185.125.190.40 80]
Holen:12 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-security InRelease [7.518 B]
Holen:13 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-updates InRelease [7.475 B]
Holen:14 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-security/main i386 Packages [216 kB]
Paketlisten werden gelesen... Fertig                      
E: Das Depot Â»[http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) xenial ReleaseÂ« enthÃ¤lt keine Release-Datei.

---

### Post by guiverc on 2022-05-30
I'd suggest using Ubuntu-MATE 18.04 LTS (*or another flavor*) as then you'll get partial support instead of minimal support.

Your issue is that because 16.04 is in ESM, it's repositories are not yet moved to *old-releases* but still in the archive.ubuntu.com.   ie. you need to reverse your change & return `old-release` to `archive`.

Don't forget the changes with an ESM release, ie.

- [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)
- [https://wiki.ubuntu.com/SecurityTeam/ESM/16.04](https://wiki.ubuntu.com/SecurityTeam/ESM/16.04)

ie. many of the packages that were supported via *deb* packages changed to *snap* only during the ESM period, such as firefox, thunderbird, libreoffice...

Ubuntu-MATE 18.04 LTS supports *i386*, and isn't yet in ESM, thus *deb* packages are still supported for many key desktop applications.

FYI:  Don't forget you can use `ubuntu-support-status` to confirm which packages are still *supported* thus get security fixes/updates etc.  Only parts of your system are supported, particularly if you didn't convert from *deb* package to *snap* package as per documentation.

---

### Post by dieter-erich on 2022-05-30
thanks a lot! Most enlightening! I am release-upgrading right now.....

---

### Post by rsteinmetz70112 on 2022-06-01
You can also go to 18.04 LTS which still has some support left.

---

