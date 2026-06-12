---
title: "Upgrade Problem not handled exepctation"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by pizeta on 2007-10-21
I tryed to upgrade from kubuntu feisty using the procedure described in the site
The update manager starts, works for a while and after downloading all the packages dies with this error

/var/log/dist-upgrade/mail.log
```

2007-10-21 13:36:14,768 DEBUG running gutsyQuirks handler
2007-10-21 13:36:14,768 DEBUG Kernel uname: '2.6.22-14-generic'
2007-10-21 13:36:15,078 DEBUG Marking 'kubuntu-desktop' for upgrade
2007-10-21 13:36:15,931 DEBUG About to apply the following changes
2007-10-21 13:36:16,149 DEBUG Held-back:
2007-10-21 13:36:16,149 DEBUG Remove:
2007-10-21 13:36:16,149 DEBUG Install:
2007-10-21 13:36:16,149 DEBUG Upgrade: openoffice.org-writer openoffice.org-draw openoffice.org-java-common openoffice.org-calc openoffice.org-style-human openoffice.org-math openoffice.org-impress python-uno openoffice.org-kde openoffice.org-common ttf-opensymbol openoffice.org-core openoffice.org-style-crystal
2007-10-21 13:36:16,152 DEBUG Free space on /: 6557048832
2007-10-21 13:36:16,152 DEBUG Dir /usr mounted on /
2007-10-21 13:36:16,152 DEBUG Free space on /var: 1384890368
2007-10-21 13:36:16,153 DEBUG Dir /boot mounted on /
2007-10-21 13:36:16,153 DEBUG Dir /var/cache/apt/archives mounted on /var
2007-10-21 13:36:16,153 DEBUG Free space on /home: 755429376
2007-10-21 13:36:16,154 DEBUG fs_free contains: '{'/var': <DistUpgradeControler.FreeSpace object at 0xa1b49ac>, '/home': <DistUpgradeControler.FreeSpace object at 0xa1b4a0c>, '/boot': <DistUpgradeControler.FreeSpace object at 0xa1b43ac>, '/usr': <DistUpgradeControler.FreeSpace object at 0xa1b43ac>, '/': <DistUpgradeControler.FreeSpace object at 0xa1b43ac>, '/var/cache/apt/archives': <DistUpgradeControler.FreeSpace object at 0xa1b49ac>}'
2007-10-21 13:36:16,167 DEBUG linux-image-2.6.20-16-generic (upgrade|installed) added with 10485760 to boot space
2007-10-21 13:36:16,200 DEBUG linux-image-2.6.22-14-generic (upgrade|installed) added with 10485760 to boot space
2007-10-21 13:36:16,316 DEBUG linux-image-2.6.20-15-generic (upgrade|installed) added with 10485760 to boot space
2007-10-21 13:36:16,390 DEBUG dir '/var/cache/apt/archives' needs '76481052.0' of '<DistUpgradeControler.FreeSpace object at 0xa1b49ac>' (1384890368.000000)
2007-10-21 13:36:16,390 DEBUG dir '/usr' needs '122880.0' of '<DistUpgradeControler.FreeSpace object at 0xa1b43ac>' (6557048832.000000)
2007-10-21 13:36:16,390 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeControler.FreeSpace object at 0xa1b43ac>' (6556925952.000000)
2007-10-21 13:36:16,391 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeControler.FreeSpace object at 0xa1b43ac>' (6504497152.000000)
2007-10-21 13:36:16,391 DEBUG dir '/' needs '10485760' of '<DistUpgradeControler.FreeSpace object at 0xa1b43ac>' (6473039872.000000)
2007-10-21 13:36:23,055 INFO using backports in '/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/backports'
2007-10-21 13:36:23,057 DEBUG have: ['/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb', '/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb']
2007-10-21 13:36:23,057 DEBUG setting MinAge to 10
2007-10-21 13:36:23,057 DEBUG setting MinAge to 10
2007-10-21 13:39:10,541 INFO cache.commit()
2007-10-21 13:40:00,572 ERROR not handled expection in KDE frontend:
Traceback (most recent call last):

  File "/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/dist-upgrade.py", line 59, in <module>
    app.run()

  File "/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/DistUpgradeControler.py", line 1328, in fullUpgrade
    if not self.doDistUpgrade():

  File "/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/DistUpgradeControler.py", line 798, in doDistUpgrade
    res = self.cache.commit(fprogress,iprogress)

  File "/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/DistUpgradeCache.py", line 69, in commit
    apt.Cache.commit(self, fprogress, iprogress)

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 215, in commit
    res = self.installArchives(pm, installProgress)

  File "/usr/lib/python2.5/site-packages/apt/cache.py", line 190, in installArchives
    res = installProgress.run(pm)

  File "/usr/lib/python2.5/site-packages/apt/progress.py", line 213, in run
    pid = self.fork()

  File "/tmp/kde-pizeta/adept_manager2cq4Nb.tmp-extract/DistUpgradeViewKDE.py", line 244, in fork
    self.child_pid = os.fork()

OSError: [Errno 12] Cannot allocate memory

2007-10-21 13:40:05,955 ERROR failed to import apport python module, can't report bug: No module named python_hook

```

After this error occurred for the first time I completed the installation with an 
apt-get dist-upgrade
apt-get autoremove
apt-get install kubuntu-desktop

Now i have a kubuntu gutsy installed but every time I open adept there is the "Version Upgrade" button
Once selected the upgrade procedure acts as described before ending with that message
What should I do in order to complete the upgrade and inform my kubuntu that i'm on gutsy ?

Thanks

---

### Post by lqyjzmms on 2007-10-23
As Marco Maini wrote on [https://bugs.launchpad.net/ubuntu/+source/adept/+bug/153975](https://bugs.launchpad.net/ubuntu/+source/adept/+bug/153975) a new version of adept has been released that fixes the last bug you are describing (the "Version Upgrade" button will disappear).

You can download adept 2.1.3-ubuntu17.1 now, e.g. from [http://archive.ubuntu.com/ubuntu/pool/main/a/adept/](http://archive.ubuntu.com/ubuntu/pool/main/a/adept/), or you can wait for a few days until the new version hits the repository of your choice.

---

