---
title: "Installing Add-On software from command line"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by jg0149 on 2007-07-25
I am getting stuck installing vmware through Adept Manager.  I need to accept the EULA and can't figure out how to do that with Adept Manager.  How can I install apps with the command line in Terminal?

---

### Post by aysiu on 2007-07-25
Close Adept completely.

Press Alt-F2

Type ```
konsole
``` This will open up a terminal.

In the terminal, paste in this command ```
sudo apt-get update && sudo apt-get install vmware-player
```

---

