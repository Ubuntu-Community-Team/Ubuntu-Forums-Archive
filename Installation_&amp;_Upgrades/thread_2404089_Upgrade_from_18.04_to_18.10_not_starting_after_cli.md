---
title: "Upgrade from 18.04 to 18.10 not starting after clicking &quot;upgrade&quot; button"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by ccrs8 on 2018-10-19
Just as the subject says.  I get a message from Software Updater saying that (x)Ubuntu 18.10 is available (I'm on 18.04), but when I click on the "Upgrade" button, nothing happens.  The message window goes away, but no upgrade window appears.  Literally nothing happens.  I can continue using my computer as normal, and if I search for updates again I get the same message, and the "upgrade" button again does nothing.  Any suggestions?  This is happening on both my desktop and laptop, so it's not limited to just one machine.

---

### Post by mdrb on 2018-10-20
Hi, I have the same issue.

---

### Post by ccrs8 on 2018-10-21
I fixed my own issue.  For some reason, the software updater GUI thought I had all of my software in 18.04 up-to-date, but in reality I was missing something.  Going to the terminal and doing
```
sudo apt-get update && sudo apt-get upgrade
```
updated a few more components.  Then going back to Software Updater took me to the same message window I got before, but this time clicking "Upgrade" worked.

---

