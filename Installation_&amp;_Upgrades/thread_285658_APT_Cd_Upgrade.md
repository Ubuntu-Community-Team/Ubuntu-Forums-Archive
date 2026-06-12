---
title: "APT Cd Upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by RudolfMDLT on 2006-10-27
Hi there,

I'm trying to Upgrade to edgy from an alternate install disc. When i add the disc to the repo's everything seems fine. I click "mark all upgrades" and then when the upgrade should begin I get this error:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Tried using upgrade manager:
gksu "sh /media/cdrom0/cdromupgrade"
and got this:

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Any ideas? How do i check whether the ISO I have was not corrupted during download or burning?

Thanks in advance for any help!

EDIT: Just got this error after the above one:

Traceback (most recent call last):

  File "/tmp/tmp.ZSC8J0/edgy", line 40, in ?
    app.run()

  File "/tmp/tmp.ZSC8J0/DistUpgradeControler.py", line 765, in run
    self.edgyUpgrade()

  File "/tmp/tmp.ZSC8J0/DistUpgradeControler.py", line 744, in edgyUpgrade
    if not self.askDistUpgrade():

  File "/tmp/tmp.ZSC8J0/DistUpgradeControler.py", line 438, in askDistUpgrade
    if not self.cache.distUpgrade(self._view):

  File "/tmp/tmp.ZSC8J0/DistUpgradeCache.py", line 251, in distUpgrade
    logging.error("Dist-upgrade failed: '%s'", e)

  File "/usr/lib/python2.4/logging/__init__.py", line 1272, in error
    apply(root.error, (msg,)+args, kwargs)

  File "/usr/lib/python2.4/logging/__init__.py", line 998, in error
    if self.isEnabledFor(ERROR):

  File "/usr/lib/python2.4/logging/__init__.py", line 1156, in isEnabledFor
    return level >= self.getEffectiveLevel()

  File "/usr/lib/python2.4/logging/__init__.py", line 1144, in getEffectiveLevel
    while logger:

KeyboardInterrupt

---

