---
title: "can't install software with Ubuntu 11.0"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by donofrij on 2011-10-19
I upgraded to Ubuntu 11.10. I was surprised to see that Synaptic Package Manager (SPM) was not installed by default, but rather has to be installed via the software center. However, when I tried to do that, I got the following error:

traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

Then, when I try to install ttf-mcorefonts-installer package, a dialog box comes up with a Microsoft license agreement that I am asked to read and accept. However, there is no place to click OK, or accept or anything else in Terminal, where it appears.

Any help/thoughts/suggestions?

---

### Post by zvacet on 2011-10-21
You can confirm licence agreement with arrow keys,and if I remember correctly you will see wite letters on red background.Then hit enter and you should be good.

---

### Post by donofrij on 2011-10-26
Thank you. It worked! Always a nice feeling :)

---

### Post by FluffWind on 2011-11-01
...license agreement? White letters on red background? 

Sorry, I'm having the same problem, but I'm totally clueless about what to to.

I hate to be bothersome, but could someone please explain a bit more detailed?

Thanks on beforehand!

Awesome, for some reason it's now working. Sorry to have bothered you!

---

### Post by tartalo on 2011-11-01
Another solution:
```
sudo apt-get install synaptic
```

---

### Post by FluffWind on 2011-11-01
Yay! Problem solved :)

---

### Post by edmatheus on 2011-11-01
> **tartalo said:**
> Another solution:
```
sudo apt-get install synaptic
```

Thank you! I got the same problem but now just fixed it.

---

### Post by thegutterpoet on 2011-11-05
I have the same problem, but the commands above donot help me.

I remain stuck with the :
[I]Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f[/I]
 message in my ubntu softwarecetre

I tryo run the apt-get install -f command, but then get told:
[I]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/I]

The details from the ubuntu software centre error message are these:
[I]The following packages have unmet dependencies:

flashplugin-installer: Depends: flashplugin-downloader (>= 11.0.1.152ubuntu1) but it is not installed
nspluginwrapper: Depends: libc6 (>= 2.4) but 2.13-20ubuntu5 is installed
                 Depends: libcurl3-gnutls (>= 7.16.2-1) but 7.21.6-3ubuntu3 is installed
                 Depends: libglib2.0-0 (>= 2.16.0) but 2.30.0-0ubuntu4 is installed
                 Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.6-0ubuntu5 is installed
                 Depends: nspluginviewer (= 1.4.4-0ubuntu3) but it is not installed
skype: Depends: ia32-libs (>= 20080808) but it is not installed
       Depends: lib32asound2 (> 1.0.24.1) but it is not installed
       Depends: lib32gcc1 (>= 1:4.1.1) but it is not installed
       Depends: lib32stdc++6 (>= 4.2.1) but it is not installed
       Depends: libc6-i386 (>= 2.4) but it is not installed[/I]

somebody please help!

---

