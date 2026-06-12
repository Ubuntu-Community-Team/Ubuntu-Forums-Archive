---
title: "Can't upgrade to Feisty Fawn"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Jaysu on 2007-05-16
So I've been stuck with this problem for a while, and I'm getting nowhere. I'm pretty sure this stemmed from a bad Ubuntu-desktop install. But here is what I get when I try to upgrade:


root@upenguin:~# gksu "update-manager -c -d"
extracting '/tmp/tmpoKskkt/feisty.tar.gz'
authenticate '/tmp/tmpoKskkt/feisty.tar.gz' against '/tmp/tmpoKskkt/feisty.tar.gz.gpg' 
could not send the dbus Inhibit signal: global name 'dbus' is not defined
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader
    if os.getuid() != 0:
NameError: global name 'os' is not defined


Any help would be much appreciated!

---

### Post by rsambuca on 2007-05-16
You can take out the -d option since Feisty is officially released now.  Actually, the recommended update method is via the update manager.  System -> Administration -> Update Manager.

You didn't specify, but I assume you are trying to update from 6.10 Edgy Eft?

---

### Post by rsambuca on 2007-05-16
Found the [[COLOR="Red"]official upgrade page[/COLOR]]("http://www.ubuntu.com/getubuntu/upgrading").

---

### Post by Jaysu on 2007-05-17
Ok, I took out the "-d" option. Yes, I am upgrading from 6.10. However, I still get the same error message. I tried to update it from the Update Manager as well, and had no luck there either. Any ideas?

---

