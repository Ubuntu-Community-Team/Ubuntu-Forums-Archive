---
title: "Change GIMP installation from PPA to snap with extras"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2018-07-27
It seems that Snap and Flatpak are the preferred replacements for PPAs, for good reason, with Ubuntu concentrating on Snap.

I currently install GIMP from the [GIMP repository]("https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp"), which allows me to also install [FONT=lucida console]gimp-gmic[/FONT] (GREYC's Magic Image Converter).

I experimented with installing GIMP via its snap, which worked well. However, I didn't know how to link [FONT=lucida console]gimp-gmic[/FONT].

How would I install GIMP via snap while also using [FONT=lucida console]gimp-gmic[/FONT]? Or should I stick to PPAs for now?

(I suppose that this question could be relevant to applications other than GIMP.)

---

### Post by 23dornot23d on 2018-11-02
I loaded gmic from the repos and these were the files in Synaptic .......... 

[IMG]https://sites.google.com/site/000menu/_/rsrc/1541120986825/wayland/problems-ubuntu-build/Screenshot%20at%202018-11-02%2002-08-01.png[/IMG]



they cause gimp to throw up a error ..........

Will go see if I can find a .deb file to load up using gdebi ........ until the repos get updated ........ as it seems the old gmic files are in there .........

       Looking around a bit more now - found this
 [https://gimpchat.com/viewtopic.php?f=8&t=16609](https://gimpchat.com/viewtopic.php?f=8&t=16609)
      


[IMG]https://sites.google.com/site/000menu/_/rsrc/1541115567794/wayland/problems-ubuntu-build/Screenshot%20at%202018-11-02%2000-38-37.png[/IMG]


Will try this link ........... see if it works .............

[URL="https://gmic.eu/gimp.shtml"]https://gmic.eu/gimp.shtml
[/URL]
```

root@base-K53SV:/home/base/Downloads# gdebi gmic_ubuntu_bionic_amd64.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

GREYC's Magic for Image Computing
 G'MIC is a full-featured open-source framework for image processing.
 It provides several different user interfaces to convert/manipulate/filter/visualize
 generic image datasets, ranging from 1d scalar signals to 3d+t sequences of
 multi-spectral volumetric images, including 2d color images.
 .
 This package contains the command-line tool (gmic), the plug-in for gimp (gmic_gimp),
 the library file (libgmic) and the webcam gui (zart).
Do you want to install the software package? [y/N]:y
Selecting previously unselected package gmic.
(Reading database ... 398065 files and directories currently installed.)
Preparing to unpack gmic_ubuntu_bionic_amd64.deb ...
Unpacking gmic (2.4.1) ...
Setting up gmic (2.4.1) ...
Processing triggers for libc-bin (2.28-0ubuntu1) ...
Processing triggers for man-db (2.8.4-2) ...


```

Now synaptic looks like this

[IMG]https://sites.google.com/site/000menu/_/rsrc/1541159125852/wayland/problems-ubuntu-build/Screenshot%20at%202018-11-02%2012-41-32.png[/IMG]


and gmic works ok again ..........


[IMG]https://sites.google.com/site/000menu/_/rsrc/1541159180037/wayland/problems-ubuntu-build/Screenshot%20at%202018-11-02%2012-43-25.png[/IMG]

---

### Post by Paddy Landau on 2018-11-02
Ah, that's excellent! Thank you for sharing your solution.

---

### Post by 23dornot23d on 2018-11-02
Your Welcome .......... ;)

Maybe some of the servers are not uptodate yet or its still at the old version on the main repos - for the problem will persist for anyone needing it ........ as what we both have done is to use our own workarounds - it really needs the main repo updating with the newer file.

Onward ....... to the next problem ....... the beauty of upgrading ....... :D

I did ask on another forum why the files are not uptodate and got this response back ........... do not know for sure who maintains them though.

> 
Ubuntu takes care only of the packages that belongs to the &#8220;main&#8221; repo  (the repository related with the Canonical business), the other packages  available in the &#8220;universe&#8221; repo are community-maintained which means  no one takes care of that .


---

