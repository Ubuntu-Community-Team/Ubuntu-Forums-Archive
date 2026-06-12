---
title: "Upgrading to 10.04 LTS amd 64"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by esky64 on 2010-06-26
Hi All
I'm using Ubuntu 9.10 and have a few problems eg can start update manager, Software centre software sources. So I wish to upgrade to 10.04LTS AMD 64.
I have set my system to dual boot ubuntu/windows with a large partition where my Home folder is placed Ubuntu/Windows both use same partition. I have never done a upgrade with system like this so Question is  how do I make sure that the upgrade leaves system the same I wish to not format Ubuntu/windows partition and leave it as my home folder.
Hope what I have written makes sense
Thanks

---

### Post by esky64 on 2010-06-29
Just tried this bit no good as you can see


chris@chris-desktop:~$ sudo do-release-upgrade
[sudo] password for chris: 
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool   27s 
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
Traceback (most recent call last):
  File "/tmp/tmpphopJU/lucid", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpphopJU/DistUpgradeMain.py", line 39, in <module>
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmpphopJU/DistUpgradeController.py", line 46, in <module>
    from DistUpgradeQuirks import DistUpgradeQuirks
  File "/tmp/tmpphopJU/DistUpgradeQuirks.py", line 39, in <module>
    from computerjanitor.plugin import PluginManager
  File "/tmp/tmpphopJU/computerjanitor/__init__.py", line 44, in <module>
    from file_cruft import FileCruft
  File "/tmp/tmpphopJU/computerjanitor/file_cruft.py", line 20, in <module>
    _ = computerjanitor.setup_gettext()
  File "/tmp/tmpphopJU/computerjanitor/__init__.py", line 39, in setup_gettext
    t = gettext.translation(domain, localedir=localedir, fallback=True)
  File "/usr/lib/python2.6/gettext.py", line 493, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))

---

### Post by dino99 on 2010-06-29
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

