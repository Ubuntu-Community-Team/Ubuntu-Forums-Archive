---
title: "&quot;python2.6 error 2&quot; after alpha3 install and updates"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hype on 2010-03-13
Hi there,
I just tried installing Lucid Alpha 3 and after trying to update system after first reboot, i get a python2.6 related bug: "le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2"
which traslates in 
"the installed post-installation sub-process script returned a type 2 error output"
 
 So, i guess some python updates are not yet on update servers so the whole install process is blocked:
ly question is, where can i "track" when this critical updates is release so that i can try to install Lucid again?

---

### Post by scaine on 2010-03-13
The only build status page I know of is on launchpad.

[https://launchpad.net/ubuntu/lucid/+builds](https://launchpad.net/ubuntu/lucid/+builds)

---

### Post by Yofel on 2010-03-13
Hey Hype. Can you post a bit more of the error message? 'sudo apt-get upgrade' in the terminal should give more output. dpkg returned exit status 2 can mean several things (usually an update-alternatives error or exec format error though)

I don't think that has anything to do with the build state, as apt shouldn't even try to install the package in this case.

---

### Post by hype on 2010-03-13
Hi,
i got the same error message than this guy [http://ubuntuforums.org/showthread.php?t=1323017](http://ubuntuforums.org/showthread.php?t=1323017)

The problematic package for me wasnt wine but python2.6 (i also had an issue with mono-common, but that didnt prevent me to update everything else).

---

### Post by hype on 2010-03-13
Ok, it seems the problem is resolved...
I updated my Lucid iso image, formatted and reinstalled with no issues

---

