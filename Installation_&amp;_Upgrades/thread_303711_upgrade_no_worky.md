---
title: "upgrade no worky"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by thebrade on 2006-11-20
I ran the upgrade command: gksu "update-manager -c"

I click upgrade in the box that pops up, then this output happens on my terminal:

[INDENT]extracting '/tmp/tmppvWWJT/edgy.tar.gz'
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
IOError: [Errno 2] No such file or directory: '/tmp/tmppvWWJT/edgy.tar.gz'[/INDENT]



any ideas?

---

### Post by deepwave on 2006-11-20
Hmm... looks a problematic/corrupt temporary file.  And update-manager chokes on it.  You could rm '/tmp/tmppvWWJT/edgy.tar.gz' and trying to run the update-manager again.

You can also use the console, and do sudo apt-get dist-upgrade.

---

