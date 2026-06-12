---
title: "Problems with update from 7.04 to 7.10"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by DoktorNo on 2008-02-19
I tryed to upgrade the 7.04 to 7.10, by using the updated-manager, as it is advised. It is starting, and then I choosed the distro upgrade. Update manager is downloading some two files, ad after that nothing happens...

```
user@host-10:~$ update-manager -c
/usr/lib/python2.5/site-packages/UpdateManager/Common/SimpleGladeApp.py:335: GtkWarning: Failed to set text from markup due to error parsing markup: B&#313;&#8218;Ä&#8230;d w wierszu 1 przy znaku 68: Element "b" zosta&#313;&#8218; zamkniÄ&#8482;ty, lecz aktualnie otwartym elementem jest "big"
  return gtk.glade.XML(self.glade_path, root, domain)
extracting '/tmp/tmpjxAo9Z/gutsy.tar.gz'
authenticate '/tmp/tmpjxAo9Z/gutsy.tar.gz' against '/tmp/tmpjxAo9Z/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: global name 'dbus' is not defined
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader
    if os.getuid() != 0:
NameError: global name 'os' is not defined
```

I also tryied to do the same with 'sudo', and the result was the same...

---

### Post by DoktorNo on 2008-02-19
*bump*

Nobody knows?

---

### Post by DoktorNo on 2008-02-23
*bump*

Three days, and nobody knows?

---

### Post by capink on 2008-02-23
I cannot help with update-manager as I don't use it. But you can try upgrading using the terminal as follows:

1. Replace all instances of feisy to gutsy in the sources.list using the following command:

```
sudo sed -i 's/feisty/gutsy/g' /etc/apt/sources.list
```

2. Update the package lists:

```
sudo apt-get update
```

3. Upgrade using the following command:

```
sudo apt-get dist-upgrade
```

---

