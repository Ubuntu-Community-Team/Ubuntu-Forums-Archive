---
title: "Can not install a deb package"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by Eremis on 2011-03-12
Hi guys,

My flash kept crashing, so I figured I would reinstall it... Firstly I deleted flash in KPackage manager (Synaptic like manager in kubuntu), then I downloaded the 32 bit from the adobe website (deb file).

Now here is where I messed up, instead of downloading that file I should have used a repository with a 64 bit version...

I installed that 32 bit package on my 64 bit machine with "--force architecture" parameter... This did not fix my flash, now it does not play flash at all... After that I figured I would just install the "correct" 64 bit version from the repos., but now I cant, because of a "package conflict"  error I keep getting, when I try to install

```

username@linux-machine:/var/cache/apt/archives$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.1kB of archives.
After this operation, 188kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.2.152.27ubuntu0.10.10.1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.2.152.27ubuntu0.10.10.1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.2.152.27ubuntu0.10.10.1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.2.152.27ubuntu0.10.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

When I try installing the package by double clicking, the same error occurs...

I dont know how to get rid of that 32 bit package, I tried everything I thought of, nothing helps

Plz Help!

---

### Post by Zorael on 2011-03-13
```
dpkg: regarding .../flashplugin-installer_10.2.152.27ubuntu0.10.10.1_amd64.deb containing flashplugin-installer:
 **adobe-flashplugin conflicts with flashplugin-installer**
  flashplugin-installer (version 10.2.152.27ubuntu0.10.10.1) is to be installed.
```
So let's get rid of that one.
```
$ sudo dpkg --purge adobe-flashplugin
```

Also this is just the kind of thing that working with **aptitude** instead of with **apt-get** would solve. When faced with dependency issues aptitude will offer you solutions, while apt-get just freaks out and exits.

---

### Post by Eremis on 2011-03-13
Ok, so I got both good and bad news...

The good is:
```

sudo dpkg --purge adobe-flashplugin

```
worked...

The bad however is flash is still messed up... I installed it from the ubuntu repos now...
(See attached screenshot)
but (only in youtube) when I scroll down, or up, the video follows the scrren and always stays in the middle of the screen, even when I open a new tab the video appears on the next page... This happens both in firefox, and chrome... The old version of flesh did not do this (the one that stored vids in /tmp). I dont know if the issue is with youtube, or flash???

How would I fix it???

Thanks

---

### Post by Zorael on 2011-03-13
Is this on a 64-bit installation or 32-bit?

---

### Post by Eremis on 2011-03-13
64

---

### Post by Eremis on 2011-03-13
fixed it.....
Solution: Go to any website that uses flash, right click the element, go to settings, and disable hardware acceleration...

thx for the help thow

---

### Post by wilee-nilee on 2011-03-13
This thread may help.
[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)

---

