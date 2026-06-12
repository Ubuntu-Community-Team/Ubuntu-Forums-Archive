---
title: "upgrading to 7.04 from 6.10"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by lwhitney on 2008-10-15
hello..would love to do a clean install, but not going to happen i hope..due to all the system files(host, dhcpd.conf, lspt.conf; etc) i need to just upgrade to 7.04. i placed the [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) in the etc/apt/sources.list file, but the update manager doesn't work when i run it..is there a different place to go? do i mark out all the other entries?

please help

heres my source.list..i marked out all of the entries

[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Beta i386 (20060928)]/ edgy restricted
#deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
#deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
#deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by lwhitney on 2008-10-15
am i screwed?? anything would be greatly appreciated!

---

### Post by Joeb454 on 2008-10-15
Try not to bump your thread too soon :)

Also I would recommend installing 7.10 or later, because support for Ubuntu 7.04 ends at the end of this month (yes it's been 18 months already) :)

---

### Post by lwhitney on 2008-10-15
i am trying to do the step by step upgrade to 8.04 and keep my settings and files. when i use my original source.list, the update manager gives me the option to upgrade to 7.04. when i click this i get alot of edgy update errors

and sorry about the bump

---

### Post by gilgongo on 2008-10-15
I was in a similar postition once with Red Hat (going from 5 to 9 I think it was). In the end, it was easier to just copy over various config files from my backup as I needed them after doing a clean install. 

Upgrades are really only for going from one version to the other.

---

### Post by lwhitney on 2008-10-16
i'm not sure how much easier it would be to do teh restore option mentioned above..here is the error page from update..i've been reading the forum trying to get as close a problem..is the update from 6.10 to 7.04 no longer an option???

my /apt/source.list is below the errors if that helps

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/binary-i386/Packages.gz](http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/source/Sources.gz](http://free.linux.hp.com/~brett/seveas/freenx/dists/dapper-seveas/freenx/source/Sources.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.31 80]



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restrict$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe main multiverse rest$
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse r$
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiver$
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse $
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates universe main multive$
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Beta i386 (20060928)]/ edgy restricted
deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
#deb [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by gjoellee on 2008-10-16
> **lwhitney said:**
> i am trying to do the step by step upgrade to 8.04 and keep my settings and files. when i use my original source.list, the update manager gives me the option to upgrade to 7.04. when i click this i get alot of edgy update errors

and sorry about the bump

The easiest thing to do will be to burn all the files you need to an external hard drive, a memory stick, CD. Then do a clean install of Intrepid Ibex or Hardy Heron (It is recommended to wait to the final release of Intrepid which will be in the end of this month).

---

### Post by zvacet on 2008-10-16
@ **lwhitney**

First of all you don´t need any third party repos when you do upgrade.So make them look like this

#deb [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
#deb-src [http://free.linux.hp.com/~brett/seveas/freenx](http://free.linux.hp.com/~brett/seveas/freenx) dapper-seveas freenx
#deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
#deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


You should replace us.archive.ubuntu.com with old-releases.ubuntu.com in every line.After that 

```
sudo apt-get update && sudo apt-get upgrade
```

After that you should be able to upgrade to Feisty.

Other way to do it is 

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

```
  sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 
```

```
 sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

> If run a manual upgrade and you have apache2 and php5 installed, make sure to start apache before the upgrade (/etc/init.d/apache2 start). See bug bug #95325 for details. 
If you do not have the admin group on your system (e.g. because you upgraded all the way back from warty) it will be added during the upgrade. Make sure to add your sudo user(s) to it. 
If you have pango-libthai installed, remove it before the upgrade 
You may want to run /usr/lib/python2.5/site-packages/DistUpgrade/apt-autoinst-fixup.py (from the update-manager package) also to fix a common problem with the automatically installed information

---

