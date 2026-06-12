---
title: "rdiff-backup, keep, kubuntu-desktop configure dpkg errors"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by themercuryman on 2007-02-13
Hello all,

I have a relatively fresh ubuntu 6.10 install that has been modified with:
 
"sudo apt-get install kubuntu-desktop"


The process seems to go as designed except now whenever I try to use apt-get, aptitude, or synaptic I get errors like the ones below:

-------------------------------------------

kingmojo@loki:~$ sudo dpkg --configure -a
Setting up rdiff-backup (1.1.5-1) ...
Compiling /usr/lib/python2.4/site-packages/LanguageSelector/LocaleInfo.py ...
  File "/usr/lib/python2.4/site-packages/LanguageSelector/LocaleInfo.py", line 58
    self._languagelist[localeenv[0]] = '%s thew[6]
                                                 ^
SyntaxError: EOL while scanning single-quoted string

dpkg: error processing rdiff-backup (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of keep:
 keep depends on rdiff-backup; however:
  Package rdiff-backup is not configured yet.
dpkg: error processing keep (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on keep; however:
  Package keep is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rdiff-backup
 keep
 kubuntu-desktop
kingmojo@loki:~$    

------------------------------------------------------

I started to remove and reinstall rdiff-backup untill I realized it would have uninstalled the whole kubuntu-desktop.

Any ideas?


Thanks,

Merc

---

