---
title: "Can't upgrade from 18.04.5 LTS to 20.04 LTS - &quot;Could not calculate the upgrade&quot;"
date: 2020-11-02
forum: Installation &amp; Upgrades
---

### Post by laurin01 on 2020-11-02
Hello,
this is my first post on this forum. I've been using Ubuntu for about two years now and really like it so far. The problems I have encountered so far could all be solved by a quick web search and reading some documentation, however this one seems different.
I tried upgrading to 20.04 LTS from bionic beaver already about a month ago, and it failed, but I thought that the problem occurred because I attempted it too early.
Well, now that I tried to perform the upgrade again, and it failed again, I think that there is a bigger problem.
At first, there was an explanation attached to the error message, that the problem was likely caused by "Unofficial software packages not provided by Ubuntu", so I disabled all ppas, from the update-manager and I also placed all files in sources.list.d in a hidden folder, so I could be sure that they wouldn't be used.
But I still got the error message "Could not calculate the upgrade", now without any likely causes listed. I disabled all repositories except the main one and the corresponding update and security repositories, but the problem still persists. According to the log file from /var/log/dist-upgrade/20201102-1930/apt.log, I have 301 broken packages, but I simply don't understand how that's possible. The main.log doesn't provide any further insight, at least to me.
I have attached Screenshots of the error messages, sources.list and the apt.log and main.log from my last upgrade attempt.
I am thankful for any help that anyone can provide me with.
Thanks in advance,
Laurin
TL;DR Tried to upgrade from 18.04.5 LTS to 20.04 LTS, according to apt.log I've got 301 broken packages and no idea how to resolve this.

---

### Post by blackbird34 on 2020-11-02
Very weird. Have you tried running this command? It's used to fix missing dependencies in your system, it might spit out some errors we can learn from.  ```
sudo apt install -f
```

---

### Post by CelticWarrior on 2020-11-02
Actually you need ```
sudo apt update && sudo apt full-upgrade
``` with ALL official repositories enabled.
Post back any errors. Those MUST be corrected before release upgrading.

---

### Post by rsteinmetz70112 on 2020-11-03
This is most likely caused by a failure to fully update the existing installation prior to running the version upgrade.
If that is not the case the next step would be to disable any ppas and external repositories then update and upgrade.
If that fails then the run :
```
apt install -f
dpkg --configure -a
```

---

### Post by deadflowr on 2020-11-03
I'd look at the PPAs,
put the PPA entries back in the original folder and run
```
tail /etc/apt/sources.list.d/*
```

post the results directly.
No one wants to download attachments just to read an output.
use code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

Some PPAs require purging over just disabling them.
Purging resets any packages that were upgraded through the PPA back to the version from the Ubuntu repositories.
This is crucial for release upgrades as sometimes a PPA will have a version that is too new and breaks the upgrading ability.

---

### Post by laurin01 on 2020-11-03
Thanks for the suggestions so far, however the problem still persists. I reenabled restricted, universe and multiverse as suggested and I'm attaching screenshots of the suggested commands and here is the output from tail:
```
laurin@thinkpad-x250:/etc/apt/sources.list.d$ tail *
==> freecad-maintainers-ubuntu-freecad-stable-bionic.list <==
# deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu bionic main
# deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu bionic main

==> freecad-maintainers-ubuntu-freecad-stable-bionic.list.distUpgrade <==
# deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu bionic main
# deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu bionic main

==> freecad-maintainers-ubuntu-freecad-stable-bionic.list.save <==
# deb http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu bionic main
# deb-src http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu bionic main

==> google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> linrunner-ubuntu-thinkpad-extras-bionic.list <==
# deb http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu bionic main

==> linrunner-ubuntu-thinkpad-extras-bionic.list.distUpgrade <==
# deb http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu bionic main

==> linrunner-ubuntu-thinkpad-extras-bionic.list.save <==
# deb http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu bionic main

==> linuxuprising-ubuntu-apps-bionic.list <==
# deb http://ppa.launchpad.net/linuxuprising/apps/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/apps/ubuntu bionic main

==> linuxuprising-ubuntu-apps-bionic.list.distUpgrade <==
# deb http://ppa.launchpad.net/linuxuprising/apps/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/apps/ubuntu bionic main

==> linuxuprising-ubuntu-apps-bionic.list.save <==
# deb http://ppa.launchpad.net/linuxuprising/apps/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/apps/ubuntu bionic main

==> signal-xenial.list <==
# deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main

==> signal-xenial.list.distUpgrade <==
# deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main

==> signal-xenial.list.save <==
# deb [arch=amd64] https://updates.signal.org/desktop/apt xenial main


```
I've disabled the ppas from the update-manager, some of them were automatically disabled during the upgrade attempt and I also disabled the rest of them via the GUI. The first error messages I got indicated that they were the likely cause, but that doesn't seem to be the case, since the upgrade fails with them disabled as well. This time it didn't even finish going trough all the files but aborted after file 130 out of 135. The number of broken packages according to the apt.log also didn't change. I am really confused right now, thanks in advance for any further help and suggestions.

---

### Post by rsteinmetz70112 on 2020-11-03
From the thumbnails it looks like you've updated your existing system successfully.
Have you tried:
```
$ do-release-upgrade
```
In a terminal window?

---

### Post by laurin01 on 2020-11-03
I've run the command, it seems to be doing the same as update-manager, the error is the same, but still thanks for the suggestion.
However, the number of broken packages according to the apt.log when trying to perform the upgrade has decreased today to 220, sudo apt update && sudo apt upgrade upgraded 8 packages.
I've also opened a bug request, as i can't find any useful information about my problem that would solve it.
I hope that the rest of the "broken" packages can be fixed somehow as well, since I don't really want to perform a fresh install because I want to avoid the hassle of restoring my data from my backups.

---

### Post by rsteinmetz70112 on 2020-11-03
Basically the GUI and do-release-upgrade call the same code but sometimes the comand line gives a little more information.

With that many broken packages it's likely that a single broken package is creating problems with dependencies.
Sometimes reinstalling a single package```
 apt install <package name> --reinstall 
```will allow apt and dpkg to fix everything else.

```
apt install -f
dpkg --configure -a
```

---

### Post by laurin01 on 2020-11-04
I've written a script to reinstall all the packages that are broken according to the apt.log:
```

#!/bin/bash
apt update
apt upgrade
cat /var/log/dist-upgrade/apt.log | egrep -o "^Broken\s[a-z:\.0-9-]*" | sed "s/$
sort -u packages.txt > packages_sorted.txt
while read line; do
        apt install $line --reinstall
done < packages_sorted.txt
echo "Done"
apt install -f
dpkg --configure -a

```
The script works and reinstalls all of the "broken" packages, but it doesn't affect the upgrade process, the number of packages marked as broken still remains at 220.
I've also tried reenabling the ppas, but they are disabled automatically during the upgrade process anyways, however the number of "broken" packages is 221, so one more, with them enabled.
I really don't know what to do anymore, the only thing left for me to try imo is to uninstall any programs installed via the ppas and rerun the script and see if the number of broken packages changes.
Thanks for all the suggestions so far, I still hope that there is some way to fix this problem, so that I can finally upgrade.

---

### Post by laurin01 on 2020-11-04
This bug also doesn't just affect me, there are multiple other people that have the same problem:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bugs?orderby=-id&start=0](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bugs?orderby=-id&start=0)
However, it doesn't seem like there's a fix for this problem yet.

---

### Post by laurin01 on 2020-11-15
After manually removing all software from external sources, I still had 182 packages marked as broken. I researched further and found that 16 of these also couldn't be reinstalled. In the end, removing gqrx-sdr and gnuradio solved the problem, I think that gnuradio was the culprit. After doing so I was able to successfully upgrade to 20.04.1 LTS.

---

### Post by alpha233 on 2021-01-28
> **laurin01 said:**
> After manually removing all software from external sources, I still had 182 packages marked as broken. I researched further and found that 16 of these also couldn't be reinstalled. In the end, removing gqrx-sdr and gnuradio solved the problem, I think that gnuradio was the culprit. After doing so I was able to successfully upgrade to 20.04.1 LTS.

Same issue, I have both gqrx-sdr and gnuradio.  'sudo apt-get remove gnuradio' alone resolved the issue and allowed the upgrade to 20.04.1 LTS.  Thank you for your comment; it saved me significant time researching.

---

