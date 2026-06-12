---
title: "[SOLVED] Upgrading 8.04 to 8.10 fails"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by tinokremer on 2008-10-30
I just tried to upgrade from 8.04 LTS to 8.10. I have enabled normal release upgrades in software sources. Then I went in update-manager and did a check. No updates to install, so I clicked "Upgrade now" in the update-manager. It then shows the screen with the links and other stuff. Straight after I click on the Upgrade button, it starts downloading 2 files.

Then nothing happens anymore.

Checking the forums and websites I found out the command do-release-upgrade should be able to do the same. This is the output of that command running as root:

root@hestia:/tmp# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'intrepid.tar.gz'
authenticate 'intrepid.tar.gz' against 'intrepid.tar.gz.gpg' 
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 53, in <module>
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 220, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 185, in runDistUpgrader
    os.execv(self.script,args)
OSError: [Errno 13] Permission denied
root@hestia:/tmp# 

Something wrong on my machine?

---

### Post by tinokremer on 2008-10-30
I have found the issue myself. It turns out using tempfs on /tmp is causing the problem. I have removed that from my fstab and unmounted /tmp. Then I did the upgrade again and it worked beautifully.

---

