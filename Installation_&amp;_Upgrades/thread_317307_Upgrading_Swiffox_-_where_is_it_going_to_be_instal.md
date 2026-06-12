---
title: "Upgrading Swiffox - where is it going to be installed"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Aramis on 2006-12-12
Hi y'all,

I have recently upgraded my Laptop to Ubuntu Edgy, and to be honnest I was expecting all my software to be upgraded at the same time whereas I have noticed that I am still using SwifFox 1.5 .

SwiftFox 1.5 is currently installed in my Home folder. I have the **DEB** file for SwiftFox 2.0 but I don't feel confortable installing just yet since I do not know where it is going to be installed. I would like to avoid having multiple instances/versions of the same application on my machine as this is a recipe for desaster. In addition, I do not wish to loose my configuration and extensions.

Thus, my questions are:
1- if I install the DEB file for SwiftFox, where is this programme going to be installed ?
2- what should I do to migrate my configuration from SwiftFox 1.5 to SwiftFox 2?
3- can I instruct the installer to install the application in the place of the old version on my Home folder?

Thanks a lot,

Ar@mi$

---

### Post by scrooge_74 on 2006-12-12
If SwifFox was not installed using apt or Synaptic then you have to manually do it.  If it is in your /home folder then I imagine it was done manually

You could delete the files and then install the new version that usually does the trick

---

### Post by Aramis on 2006-12-12
Hi there Scrooge_74,

that is correct old version of SwiftFox such as v 1.5 had to be installed by hand.

I don't fancy deleting the files as it would mean that I will have to rebuild the configuration of SwiftFox from scratch :|

A.

---

### Post by scrooge_74 on 2006-12-12
Maybe you can just move the directory to another place for the time been,and then install the new version,so you don't loose config files.  You can even installed the new version using another location so you can still have both versions

---

### Post by Aramis on 2006-12-15
Right... this is really scary. To answer my own question, the debian package of SwiftFox 2.0 installs the application in **usr/bin/swiftfox**, so it is all well clear from the ad-hoc installation I have in my home folder.

I did check the difference in terms of Extension, and themes, between the default installation of FF, SF 1.5 and SF 2.0. Only to conclude that I can't tell the difference. Provided these are supported, all the extensions I use in either applications are present, and so are the themes.

My guess is that I have not change the manner in which I use FF since I installed it on my laptop in April... SW 1.5 picked up on the configuration used. When FF 2 was available only the main binaries were updated, and finally SW 2.0 just copied the configuration of the updated FF. Some what I guess I am lucky. I shall backup my SW 1.5 profile just in case, and then delete it.

Anyways, unless someone has more information on the matter I think this problem is solved.

A.

---

