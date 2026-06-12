---
title: "[SOLVED] Package Manager Updates Missing Task Bar Icons"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by djcslip on 2008-05-28
Hi,

I initially upgraded to the release candidate, and then performed a full update to 8.04.

Package manager no longer tells me that updates are waiting (in task bar) nor does the task bar icon appear when the package manager is opened, nor if the system requires a reboot.

Any ideas?

---

### Post by mxg01 on 2008-05-28
You may be missing the notification area applet which will notify you when updates are available. Select the panel where it should be, do a right click on it, select 'add to panel', scroll down until you find 'notification area' and add it to the panel. That should fix your issue with no update icon appearing.

---

### Post by djcslip on 2008-05-28
Thanks - But i'd already tried that!

Any other ideas?!

---

### Post by mxg01 on 2008-05-28
Is the update-notifier running?

If not then you can add it via System - Preferences - Sessions.

If that does not work maybe you can try reinstalling the update-notifier package.

---

### Post by djcslip on 2008-05-28
update-notifier was not installed.

Thank you very much!

---

