---
title: "E:Lists directory /var/lib/apt/lists/partial is missing."
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by Porpoise on 2007-12-23
I'm trying to upgrade from Fiesty to Gutsy but keep getting the following error:  Checking for a new ubuntu release Done downloading Traceback (most recent call last):   File "/usr/bin/do-release-upgrade", line 45, in      fetcher.run()   File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 155, in run     if not self.fetchDistUpgrader():   File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 133, in fetchDistUpgrader     if fetcher.Run() != fetcher.ResultContinue: SystemError: E:Lists directory /var/lib/apt/lists/partial is missing.  I am also getting the "E:Lists directory /var/lib/apt/lists/partial is missing" when using update manager too.  Is there somewhere I can get this missing file from? (I don't know how it's gone missing in the first place).

---

### Post by schaumkeks on 2007-12-23
Normally this directory is automatically recreated by apt. Try running ```
sudo apt-get update
``` again. If this doesn't work, please post the output of```
ls -al /var/lib/apt/lists/partial
``` or ```
ls -al /var/lib/apt/lists
```. Maybe some problem with the permissions.

---

### Post by Porpoise on 2007-12-23
Thanks.

Managed to fix it using this:

sudo mkdir -p /var/lib/apt/lists/partial

from [[IMG]http://ubuntuforums.org/customavatars/avatar60864_3.gif[/IMG]]("http://ubuntuforums.org/member.php?u=60864") 			 			 				 					 					[zanglang]("http://ubuntuforums.org/member.php?u=60864") 					

Over in "[General Help]("http://ubuntuforums.org/forumdisplay.php?f=131")" after lots of searching.


I guess that re-created the file, which then allowed the Upgrade to proceed (although there were a few issues on the way). Thankfully, I&#7743; now fully upgraded and functioning (AFAIK)


Cheers,

---

