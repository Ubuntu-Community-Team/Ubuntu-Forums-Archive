---
title: "Firefox pre releases"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by SoFl W on 2010-01-23
Somehow* I turned on pre-releases for Mozzila products and it upgraded FireFox to a pre version.  I want to know how to turn off downloading of the pre stable release versions of software.  I also need to uninstall the pre release version and download a stable version but I can figure that out (I hope)

I don't think it is important for this but I have 64bit 9.10 Studio installed.

*It has been a long week and I think I remember reading about the latest version but not sure what I did in a half asleep mode.  Currently the version of Firefox on my ubuntu machine is too unstable to use and I have to use an old Win2k laptop to get to the web.

Thank you.

(This thread is in the wrong forum, can a mod please move it)

---

### Post by Leppie on 2010-01-23
hi and welcome to the community,

> **SoFl W said:**
> Somehow* I turned on pre-releases for Mozzila products and it upgraded FireFox to a pre version.  I want to know how to turn off downloading of the pre stable release versions of software.
check you software sources. go to System>Administration>Software Sources, go to the "Updates" tab and remove the tick from "Pre-released updates (karmic-proposed)".
then run apt-get update:
```
sudo apt-get update
```> **SoFl W said:**
> I also need to uninstall the pre release version and download a stable  version but I can figure that out
check the package installed:
```
dpkg -l | grep firefox
```mine looks like this:
```
ii  firefox                                                     3.6.1~hg20100122r33533+nobinonly-0ubuntu1~umd1~karmic   safe and easy web browser from Mozilla
```so for me, the command to remove Namoroka (ff3.6 pre) would be like this:
```
sudo apt-get remove firefox
```

---

### Post by SoFl W on 2010-01-23
Thank you,

I did check the pre-release tab and it is off.  My "dpkg -l | grep firefox" command

returns:
ii  firefox  3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd2~karmic

---

### Post by Leppie on 2010-01-23
i just ran update manager and now my version is the same as yours.
so you have added the ubuntu mozilla daily ppa to your repos.
go to softwares sources, other software and remove the following entry:
```
 [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)
```

---

### Post by SoFl W on 2010-01-23
Thank you.

Earlier I removed only the gpg key, but not the software source, thank you for making me look at that again.  I can now use my ubuntu machine to access the forms.  (and the rest of the net)

Thanks again.

---

### Post by Leppie on 2010-01-24
> **SoFl W said:**
> I can now use my ubuntu machine to access the forms.  (and the rest of the net)

Thanks again.
i'm glad everything is working properly now.
though win2k is one of the most decent os's microsoft ever produced.

---

### Post by michael37 on 2010-01-25
Install Firefox 3.6 release from firefox-stable ppa: 
[http://ubuntuforums.org/showpost.php?p=8723004&postcount=11](http://ubuntuforums.org/showpost.php?p=8723004&postcount=11)

For users of daily-build, consider installing ffox36-daily-transition-special package.

---

