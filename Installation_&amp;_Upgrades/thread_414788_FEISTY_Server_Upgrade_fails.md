---
title: "FEISTY Server Upgrade fails"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by nickswift on 2007-04-20
Start the installer and this is what I get:

[FONT="Courier New"]nick@www:/etc/apt$ sudo do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool 
Done downloading            
extracting '/tmp/tmpHk0mvS/feisty.tar.gz'
authenticate '/tmp/tmpHk0mvS/feisty.tar.gz' against '/tmp/tmpHk0mvS/feisty.tar.gz.gpg' 

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Done [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Done [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Done [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release
Done [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) edgy/universe Sources
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Done [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Done downloading            

Updating repository information
**WARNING: Failed to read mirror file**


A fatal error occured
Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmpHk0mvS/feisty", line 56, in ?
    app.run()

  File "/tmp/tmpHk0mvS/DistUpgradeControler.py", line 1025, in run
    self.fullUpgrade()

  File "/tmp/tmpHk0mvS/DistUpgradeControler.py", line 962, in fullUpgrade
    if not self.updateSourcesList():

  File "/tmp/tmpHk0mvS/DistUpgradeControler.py", line 390, in updateSourcesList
    if not self.rewriteSourcesList(mirror_check=True):

  File "/tmp/tmpHk0mvS/DistUpgradeControler.py", line 302, in rewriteSourcesList
    if ((len(self.cache[pkgname].candidateOrigin) == 0)

  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 82, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-minimal'

[/FONT]

Any ideas?

---

### Post by nickswift on 2007-04-21
Fixed it - for some reason the relevant deb line was missing from sources.list

Nick

---

### Post by kc5hwb on 2007-04-21
I don't get that far.  From the update manager, I click on Upgrade to 7.04, it brings up the "about" page and I click ok, then it starts to DL the 2 files, and at the end of that it says "Authentication failed, there is either a problem with the network or the server"

---

