---
title: "Install of 13.10 beta fails"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by gerbreown1 on 2013-09-27
When I try to upgrade from 13.04 to 13.10 I get the following error: 

"gerald@gerald:~$ update-manager -d
Checking for a new Ubuntu release
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
gpg exited 127
Debug information: 


gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: UP




Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 152, in <module>
    fetcher.run()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 283, in run
    _("Authenticating the upgrade failed. There may be a "
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py", line 50, in error
    return error(self.window_main.window_main, summary, message)
AttributeError: 'NoneType' object has no attribute 'window_main'"

Are there any known fixes for this error???

Thanks.

---

