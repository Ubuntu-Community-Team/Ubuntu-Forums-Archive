---
title: "cdrom upgrade 8.04 to 10.04 fails"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by kai ekael on 2011-01-04
I'm trying to upgrade from 8.04 LTS to 10.04 via the cdrom. Network upgrade just takes way too long (hours and hours to download packages versus an hour to download the iso).

Anyway, downloaded and mounted alternate iso fine.

Running gksu "sh /mnt/iso/cdromupgrade" results in a python traceback:

[FONT="Courier New"]Traceback (most recent call last):
  File "/tmp/tmp.SWzoK17347/maverick", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmp.SWzoK17347/DistUpgradeMain.py", line 39, in <module>
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmp.SWzoK17347/DistUpgradeController.py", line 40, in <module>
    from utils import country_mirror, url_downloadable, check_and_fix_xbit, ExecutionTime
  File "/tmp/tmp.SWzoK17347/utils.py", line 26, in <module>
    apt_pkg.init_config()
AttributeError: 'module' object has no attribute 'init_config'[/FONT]

This makes sense, python-apt doesn't have this method:

[FONT="Courier New"]Python 2.5.2 (r252:60911, Jan 20 2010, 21:48:48) 
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import apt_pkg
>>> apt_pkg.init_config
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'init_config'[/FONT]

My guess is it's an issue of newer version of python-apt expected by the script. Anyone run into this and have a work around? Really don't want to spend 10 hours download packages again. :|

---

