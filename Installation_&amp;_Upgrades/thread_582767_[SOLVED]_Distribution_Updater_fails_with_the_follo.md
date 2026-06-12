---
title: "[SOLVED] Distribution Updater fails with the following error."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by perlluver on 2007-10-20
Traceback (most recent call last):
  File "/tmp/kde-perlluver/adept_managerXLDvrb.tmp-extract/dist-upgrade.py", line 59, in <module>
    app.run()
  File "/tmp/kde-perlluver/adept_managerXLDvrb.tmp-extract/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()
  File "/tmp/kde-perlluver/adept_managerXLDvrb.tmp-extract/DistUpgradeControler.py", line 1312, in fullUpgrade
    if not self.askDistUpgrade():
  File "/tmp/kde-perlluver/adept_managerXLDvrb.tmp-extract/DistUpgradeControler.py", line 711, in askDistUpgrade
    if not self.cache.distUpgrade(self._view, self.serverMode, self.logfd):
  File "/tmp/kde-perlluver/adept_managerXLDvrb.tmp-extract/DistUpgradeCache.py", line 452, in distUpgrade
    if not origin.trusted:
UnboundLocalError: local variable 'origin' referenced before assignment

---

