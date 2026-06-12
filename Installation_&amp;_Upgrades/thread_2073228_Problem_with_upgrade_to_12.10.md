---
title: "Problem with upgrade to 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by obi007 on 2012-10-19
Hi 

I was a problem with upgrade my ubuntu 12.04 to 12.10

When I do as root
 do-release-upgrade -d

After update and downloading the packets I get i error:


Sprawdzanie mened&#380;era pakietów
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Przetwarzanie zmian

Przetwarzanie zmian

Nie mo&#380;na przetworzy&#263; aktualizacji 

Wyst&#261;pi&#322; nierozwi&#261;zywalny problem podczas obliczania aktualizacji: 
E:Unable to correct problems, you have held broken packages. 

Mo&#380;e to by&#263; spowodowane przez: 
* aktualizowanie do testowej wersji Ubuntu, 
* u&#380;ytkowanie bie&#380;&#261;cej testowej wersji Ubuntu, 
* u&#380;ytkowanie nieoficjalnych pakietów spoza repozytoriów Ubuntu. 

Je&#347;li &#380;adna z wymienionych sytuacji nie ma miejsca, prosz&#281; zg&#322;osi&#263; 
ten b&#322;&#261;d wprowadzaj&#261;c w terminalu polecenie „ubuntu-bug 
ubuntu-release-upgrader-core”. 


Przywracanie pierwotnego stanu systemu

Anulowanie
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Whats a problem ? What I must to do ?
Please help.

---

### Post by 2F4U on 2012-10-19
In order to  get better responses, you should probably provide the output in English language.

---

### Post by obi007 on 2012-10-20
When I change language in my system from Polish to English, and when i do:  do-release-upgrade -d

I get:

i# do-release-upgrade -d
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                                                                                                 
Get:2 Upgrade tool [1,200 kB]                                                                                                                        
Fetched 1,200 kB in 0s (0 B/s)                                                                                                                       
authenticate 'quantal.tar.gz' against 'quantal.tar.gz.gpg' 
extracting 'quantal.tar.gz'



Error in sys.excepthook:
Traceback (most recent call last):
  File "/tmp/update-manager-KeJL0Y/DistUpgrade/DistUpgradeViewText.py", line 99, in _handleException
    "\n".join(lines))
  File "/tmp/update-manager-KeJL0Y/DistUpgrade/DistUpgradeViewText.py", line 133, in error
    print(twrap(summary))
UnicodeEncodeError: 'ascii' codec can't encode character u'\u0105' in position 4: ordinal not in range(128)

Original exception was:
Traceback (most recent call last):
  File "/tmp/update-manager-KeJL0Y/quantal", line 10, in <module>
    sys.exit(main())
  File "/tmp/update-manager-KeJL0Y/DistUpgrade/DistUpgradeMain.py", line 227, in main
    app = DistUpgradeController(view, options, datadir=options.datadir)
  File "/tmp/update-manager-KeJL0Y/DistUpgrade/DistUpgradeController.py", line 114, in __init__
    self._view.updateStatus(_("Reading cache"))
  File "/tmp/update-manager-KeJL0Y/DistUpgrade/DistUpgradeViewText.py", line 113, in updateStatus
    print(msg)
UnicodeEncodeError: 'ascii' codec can't encode character u'\u0119' in position 17: ordinal not in range(128)

---

### Post by obi007 on 2012-10-20
I think the problem could be in my sources

cat /etc/apt/sources.list
# Ubuntu - podstawowe repozytoria
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted universe multiverse

# GetDeb
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) precise-getdeb apps games

# Ubuntu Tweak
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main

# Wine
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main

# Chromium (stabilne)
deb [http://ppa.launchpad.net/chromium-daily/stable/ubuntu](http://ppa.launchpad.net/chromium-daily/stable/ubuntu) precise main

# XBMC
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) precise main

# VirtualBox
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib

#Google
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports restricted multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security restricted

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

