---
title: "Help to download from repositories to CD"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by Matchless on 2005-06-13
Hi,
    Is it possible to download applications from the repositories and store on a CD to install later? Preferably with a Windows PC. Using Kynaptic takes the Kubuntu box out of service for hours on a dialup line and if you reinstall Kubuntu the app is gone and has to be downloaded again. There must be an easy way!
Thanks
Matchless

---

### Post by desdinova on 2005-06-13
[QUOTE=Matchless]Hi,
    Is it possible to download applications from the repositories and store on a CD to install later? Preferably with a Windows PC. Using Kynaptic takes the Kubuntu box out of service for hours on a dialup line and if you reinstall Kubuntu the app is gone and has to be downloaded again. There must be an easy way!
Thanks
Matchless[/QUOTE]
 Not really as they're pretty huge - but you could always backup /var/cache/apt and save the files you've downloaded

---

### Post by tread on 2005-06-13
When you install packages, they get stored in /var/cache/apt .. you can retrieve them from there and burn them to a cd. Using a windows machine is tricky because you will need to make sure you have all the dependencies, otherwise its wasted effort.

---

### Post by tread on 2005-06-13
Oh, another thing .. I've never used kynaptic so just make sure it doesnt clean out the cache each time by default. If it does that you can use aptitude.

---

### Post by Matchless on 2005-06-13
Thanks, replies within less than a minute of posting question!!! All I can say is INCREDIBLE!
I will try and copy the cache as suggested, just have to get Unbuntu reinstalled again!
Thanks again!

---

