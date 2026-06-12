---
title: "Unistalling City Lens"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by Liamdale on 2014-05-05
Hi everyone

A week ago I queried this forum on how to get the city lens that I installed, to work.  Unfortunately no one could help me.  Could someone give me the terminal instructions to uninstall the city lens.


Liamdale

---

### Post by bapoumba on 2014-05-06
I suppose this is your thread : [http://ubuntuforums.org/showthread.php?t=2220077](http://ubuntuforums.org/showthread.php?t=2220077)

There are 2 ways of doing this :

1- install ppa-purge (from the universe repositories, there is a package for Quantal 12.10) and run
```
sudo ppa-purge ppa:<ppa_name>
```

2- manually uninstall the packages and remove the ppa :
```
sudo apt-get remove --purge unity-lens-utilities unity-scope-cities
```
Then remove the ppa from /etc/apt/sources.list.d

Just to make sure about the ppa exact name, what does return :
```
ls /etc/apt/sources.list.d
```

---

### Post by Liamdale on 2014-05-06
Hi Bapoumba;

Yes, this thread is related to : [http://ubuntuforums.org/showthread.php?t=2220077](http://ubuntuforums.org/showthread.php?t=2220077)

My current version of ubuntu is 12.04 LTS.  I am studing the best way to upgrade to 14.04 LTS

Your first option suggestes that "ppa-purge" is an apt that I must install before I can use it.  If that is the case then I assume the instruction should be
```

sudo add-apt-repository ppa:ppa-purge/ppa

```

The second option you state > Then remove the ppa from /etc/apt/sources.list.d
I assume you mean > scopes-packagers-ppa-precise.list from the directory list stated below

> getdeb.list
getdeb.list.save
otto-kesselgulasch-gimp-precise.list
otto-kesselgulasch-gimp-precise.list.save
scopes-packagers-ppa-precise.list
snwh-moka-gtk-theme-daily-precise.list
snwh-moka-gtk-theme-daily-precise.list.save
snwh-moka-icon-theme-daily-precise.list
snwh-moka-icon-theme-daily-precise.list.save


As you can see, I'm new at this but I'm slowly but surely getting it

Liamdale

---

### Post by bapoumba on 2014-05-06
[http://packages.ubuntu.com/search?suite=precise&searchon=names&keywords=ppa-purge](http://packages.ubuntu.com/search?suite=precise&searchon=names&keywords=ppa-purge)
ppa-purge is in the universe repos for 12.04 (sorry I sort of mixed up the releases code names..), so you just install it and run 
sudo ppa-purge ppa:<ppa_url>

You can find the url with :
cat /etc/apt/sources.list.d/scopes-packagers-ppa-precise.list

On a side note, should you upgrade to 14.04, please remove all you ppa before doing so. Some play well with upgrades, some do not.

---

### Post by Liamdale on 2014-05-06
Tried to use ppa-purge.  The terminal output seemed to indicate succes but cities scope was still listed in my list of installed packages.
(used  dpkg --get-selections | grep -v deinstall > ~/Desktop/packages)

Finally used second option
```
sudo apt-get remove --purge unity-lens-utilities unity-scope-cities
```

and this worked.  removed the utilities lens, cities scope and the calculator scope

Although I never got the cities scope to work (odd the calculator worked) I must consider this thread as solved.

Thanks Bapoumba

---

### Post by bapoumba on 2014-05-06
Glad to see you got it to work :)
Please remember to disable all you other ppas should you choose to upgrade.

---

