---
title: "Computer crashed during Upgrade"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by RBCBrooklyn on 2011-11-25
[COLOR=#000000]Just to preface I've been using linux for about a year and a half but never got to heavy in the programming side. So you can consider me an educated n00b.[/COLOR]
[COLOR=#000000] [/COLOR]
[COLOR=#000000]I was upgrading from ubuntu 11.04 to 11.10 on my computer when I made my first mistake of trying to check my email on chrome. The upgrade then started to crash  reporting "error adding" to every item and seemingly grind to a halt. The only recourse at the time seemed to be to restart (second mistake.)[/COLOR]
[COLOR=#000000] [/COLOR]
[COLOR=#000000]The computer now will only boot up in terminal language not to my desktop. I tried running ubuntu off iso cds (desktop, server and alternative) to no avail. Desktop cd couldn't find the bootarg and the other iso cd's recovery of broken system just leads me back to the same issues I have if I boot up without it (programming code with no results.)[/COLOR]
[COLOR=#000000] [/COLOR]
[COLOR=#000000]It still knows my username and password on top of it informing me I have 750 items needing upgrades so that gives me hope that all my info isn't lost.  I tried accessing the upgrade manager but it says its not available. I'm looking for an alternative to reinstalling ubuntu and losing all my files. Any suggestions on how to restart the upgrading process or some way to fix this? Thanks. Please let me know if more info is required.[/COLOR]
[COLOR=#000000]-RBC[/COLOR]

---

### Post by BlouBlou on 2011-11-25
Try this commands: ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```And this one too: ```
sudo do-release-upgrade
```

---

