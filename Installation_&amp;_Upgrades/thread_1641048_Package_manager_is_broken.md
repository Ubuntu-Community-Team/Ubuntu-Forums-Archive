---
title: "Package manager is broken"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by maxrpowell on 2010-12-08
I just installed brother DCP-350c drivers from [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090")
When I finished I tried to install a scanner driver from brother.
My package manager is broken.
The page mentioned something about that [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090")(just a scroll down)
I tried what they said but the manager is still broken.
It gives me this error report:

> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the dcp350clpr package. This might mean you need to manually fix this package.


Ubuntu 10.10 on Toshiba Satellite

---

### Post by maxrpowell on 2010-12-08
actually it looks as if all I must do is uninstall package dcp350clpr
i cannot use sudo apt-get remove dcp350clpr
b/c package manager is broken

---

### Post by maxrpowell on 2010-12-08
how can i do that?

---

### Post by sikander3786 on 2010-12-09
Go to Applications > Accessories > Terminal and post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

