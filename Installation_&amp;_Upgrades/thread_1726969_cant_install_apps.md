---
title: "cant install apps"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by ironchefchopchop on 2011-04-11
> An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

details-

> Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.



plz help, me noob

---

### Post by lmarmisa on 2011-04-11
Welcome to the Forums.

Maybe this thread could help you:

[http://ubuntuforums.org/showthread.php?t=1632545](http://ubuntuforums.org/showthread.php?t=1632545)

Best regards,

Luis

---

### Post by ironchefchopchop on 2011-04-11
i type-
>  sudo apt-get update && sudo apt-get upgrade

it says at the bottom-
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by rosencrantz on 2011-04-11
If Synaptics or something related is not running, you can try this
> **dreadlord_chris said:**
> if you're sure that no apt/adept/dpkg processes are running:
```

sudo rm /var/lib/dpkg/lock

```
Should take care of your little problem...

---

### Post by ironchefchopchop on 2011-04-11
```
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

```

---

### Post by rosencrantz on 2011-04-11
You could try removing that lock, too. Someone on the Interwebs suggests 
sudo killall apt-get
which can't hurt either.

---

### Post by ironchefchopchop on 2011-04-12
still not working :cry:

---

### Post by rosencrantz on 2011-04-12
I hope you have rebooted by now... Did that help?
[http://www.youtube.com/watch?v=p85xwZ_OLX0](http://www.youtube.com/watch?v=p85xwZ_OLX0)

---

