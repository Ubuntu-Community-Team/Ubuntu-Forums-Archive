---
title: "Feisty to Gutsy upgrade aborts - dependency problems"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by analyzer123 on 2007-10-21
Hello all,
    I tried upgrading from feisty to gutsy today, with disastrous results. I used the update-manager from the gnome administration and said upgrade.

1) all files were downloaded correctly
2) installation went till about 60%
3) after this, it started giving dependency errors, saying certain modules could not be installed, which included:
gnome-themes
ubuntu-desktop

There were 2-3 popups in the middle, with the same kind of errors, but finally the upgrade just aborted and said to check the logs, and report a bug under "update-manager"

The final error is in:
ImportError: No module named apport
Could not import module, is a package upgrade in progress? Error: /var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so: undefined symbol: g_timeout_add_seconds_full

I have truncated the log files and have attached it to this post. 

Now I am left with an unstable system. If I boot it, gnome doesnt start up. I can login thru the text console, but essentially cant do anything.

System: dell e1405, originally: feisty

Please help!
Thanks

---

