---
title: "why won't youtube work?..."
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by iScience on 2013-06-01
some videos on youtube play just fine while others display this error message;

> 
the adobe flash player is required for video playback Get the latest Flash Player


i went to the link that it gave me and i got the gzip file for flash. i gunzipped and did tar xvf. and then i restarted my firefox browser. youtube is still not working; please help.

---

### Post by oldos2er on 2013-06-01
Let the package manager install it: ```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by iScience on 2013-06-01
Question:    in the past when youtube didn't work, i did the following

```

$ sudo apt-get update
$ sudo apt-get upgrade

```

i thought upgrade installed all the updates downloaded. am i mistaken?

the commands you told me to enter in worked; but does that mean that i have to install every update individually? or is there a command where i can install everything i just downloaded? i thought "upgrade" was that command.

---

### Post by ajgreeny on 2013-06-01
What you did was download and unpack the archive of flashplayer; you did not install it so it is still just sitting in whichever folder you unpacked it to.

The update commands you mention do not install unpacked archives that you've downloaded; that's not the way Ubuntu or Linux works, they simply check for updates of, and then upgrade any packages that are already installed in your system for which newer versions are available.

---

### Post by Frogs Hair on 2013-06-01
Flash is not installed by default on most operating systems. Now that you have installed Flash with the plug-in installer it will get security updates via the software updater. Some videos are now using the HTML5 format and many still require Flash this is the reason some will play without Flash.  [http://en.wikipedia.org/wiki/HTML5](http://en.wikipedia.org/wiki/HTML5)

---

