---
title: "unable to start X after upgrade"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by satimis on 2012-05-06
Host - ubuntu 11.04 desktop
VM - ubuntu 10.04 desktop
Virtualizer Oracle VirtualBox

After upgrade the VM to 12.04 LTS, on reboot only a black sreen was displayed.

Drop to root shell on restart

# startx /usr/bin/gnome-session
Faital server error:
Could not create lock file in /tmp/.tX0-lock
...
ddxSikGiveUp: Closing log

# ls -l /tmp```

drwx----- 2 root root 4096 ....

```

# chmod 1777 /tmp```

chmod: changing permisions of '/tmp': Read-only file system
```

Pls help.  TIA

B.R.
satimis

---

