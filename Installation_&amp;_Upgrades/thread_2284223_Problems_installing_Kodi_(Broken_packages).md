---
title: "Problems installing Kodi (Broken packages)"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by conor7 on 2015-06-27
I have just recently started using Ubuntu so I dont really know how to use it properly yet.
The reason for downloading it is I am try to download Kodi (xbmc) but when it comes to entering 

> sudo apt-get install kodi


It comes up saying I have broken packages.

> sudo apt-get install kodi
[sudo] password for conor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 kodi : Depends: kodi-bin (>= 2:14.2~git20150327.1058-final-0precise) but it is not installable
        Depends: kodi-bin (< 2:14.2~git20150327.1058-final-0precise.1~) but it is not installable
        Depends: libshairplay0 but it is not installable
        Depends: libcec2 (>= 2.1.1) but it is not installable
        Recommends: libva-intel-vaapi-driver but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I've got something called Synaptic Package Manager, when I go to mark Kodi for installation it says broken package. When I try to fix broken packages I get a message saying... 

> E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies




Looked on forums seen some people saying to do - sudo apt-get update 
but this doesn't make a difference.
Can anyone help me out please, would be much appreciated.

---

### Post by coldraven on 2015-06-28
Sometimes the Software Centre is a bit out of date so you can install the latest version of programs by adding repositories. See here:
[http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux#Installing_Kodi_on_Ubuntu-based_distributions](http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux#Installing_Kodi_on_Ubuntu-based_distributions) 
```
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install kodi
```

Disclaimer: I have not tried this myself, I use Kodi on a Raspberry Pi2. (It's very good!)
Also, only add repositories from people that you trust! (I think that Kodi are trustworthy)

More info on repositories here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

