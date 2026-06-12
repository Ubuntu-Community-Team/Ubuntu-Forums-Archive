---
title: "New install sytem freezes"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by gerrylerner on 2009-11-23
Just installed 9.10, splitting with the existing WindowsXP. On reboot all was well until I right clicked with the mouse This froze everything. Switched off and rebooted and the same happened. Tried rebooting in WindowsXP and the mouse worked fine.

Is there anything I can do to rescue 9.10?

---

### Post by lemming465 on 2009-11-24
Keep away from the mouse, use Ctrl-Alt-F1 to switch to a text console, log in, and run```
sudo -i
aptitude update
aptitude full-upgrade
```

That might pull down a bug fix for your mouse-induced crash.  If not, you may have to try an older version such as 9.04, or wait for 10.04, or try a different distributions, or something.

---

### Post by gerrylerner on 2009-11-25
> **lemming465 said:**
> Keep away from the mouse, use Ctrl-Alt-F1 to switch to a text console, log in, and run```
sudo -i
aptitude update
aptitude full-upgrade
```

That might pull down a bug fix for your mouse-induced crash.  If not, you may have to try an older version such as 9.04, or wait for 10.04, or try a different distributions, or something.
Thanks. Tried this but it made no difference.

---

