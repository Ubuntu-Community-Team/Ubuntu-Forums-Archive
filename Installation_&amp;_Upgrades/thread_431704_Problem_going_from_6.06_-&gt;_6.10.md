---
title: "Problem going from 6.06 -&gt; 6.10"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by luken8r on 2007-05-03
Im trying the "Official Upgrade Method" to get to 7.04 from my curretn 6.06, so the first step is to go to 6.10, right?
I go to the upgrade manager via:

gksu "upgrade-manager -c"

This fires up the upgrade manager as it should so I hit the Upgrade button, however the install dies after a second with the following output:
> 
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpbwbbfR/edgy.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 641, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.4/site-packages/UpdateManager/DistUpgradeFetcher.py", line 211, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.4/site-packages/UpdateManager/DistUpgradeFetcher.py", line 136, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.4/tarfile.py", line 921, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.4/tarfile.py", line 964, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpbwbbfR/edgy.tar.gz'


What gives??

---

### Post by luken8r on 2007-05-04
Anyone know what is going on here?

---

