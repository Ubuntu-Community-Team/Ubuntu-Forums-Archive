---
title: "Question about repositories"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by RedSuisei on 2011-02-06
Hello, I'm newbie at using Ubuntu here. Dunno if this is the right section to ask about this, but I have question regarding additional repositories.  I found a lot of PPA with unofficial builds or latest builds of certain packages which the official/older builds are available on the default repo. If I added these PPA, wouldn't that mean one package name is available from different repos? So how do apt-get or aptitude pick which repo to get the package?  Thanks in advance.

---

### Post by ajgreeny on 2011-02-06
The default settings mean that if the ppa has a newer version of the package than the official repos, the newer version will be installed when you update or add a package.  If you want to keep a particular version lower than the ppa's you can pin the system to keep packages quite easily.

---

### Post by RedSuisei on 2011-02-06
Hmm, how about things like unofficial builds etc?  And how do I pin the system like you said? Sounds interesting :)

---

### Post by ajgreeny on 2011-02-06
In synaptic you can choose Package >Lock version in the menus, after installing a package, or you can do it system wide with 
 To pin a package version add these lines to  /etc/apt/preferences:
```
Pin: Package: name (no version number here)               
version (number showing as installed in synaptic)    
Pin-Priority: 1001
```
I would normally say keep away from unofficial builds, whatever that may mean.  Some people think the ppas are unofficial, but used with care they can be very useful.  At this stage just don't use any system packages from a ppa, eg xorg or similar or you could come unstuck and need to put things right in recovery mode, as I had to today.  easy enough if you know what you're doing, but probably a show-stopper for a new user.

You are probably OK to try GUI applications eg gthumb, vlc, etc, as if they don't work you can simply uninstall, disable the ppa from which they came and then reinstall.

---

