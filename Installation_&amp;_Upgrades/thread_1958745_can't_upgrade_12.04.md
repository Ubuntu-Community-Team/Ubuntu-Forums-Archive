---
title: "can't upgrade 12.04"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by closbar on 2012-04-14
already installed 12.04 but can not upgrade 
I run update-manager -d and update manager box shows with another box 
"Not all updates can be installed" 
run partial upgrade, to install as many updates as posible 
and 
 I run partial upgrade 
and another box with this:
[COLOR=Black]CAN NOT UPGRADE
an upgrade from `precise`to `oneiric` is not supported with this tool
[/COLOR]
the sudo apt-get upgrade 
shows 293 packages not upgrade
Thanks for any help

---

### Post by zombifier25 on 2012-04-15
> **closbar said:**
> already installed 12.04 but can not upgrade 
I run update-manager -d and update manager box shows with another box 
"Not all updates can be installed" 
run partial upgrade, to install as many updates as posible 
and 
 I run partial upgrade 
and another box with this:
[COLOR=Black]CAN NOT UPGRADE
**an upgrade from `precise`to `oneiric` is not supported with this tool**
[/COLOR]
the sudo apt-get upgrade 
shows 293 packages not upgrade
Thanks for any help
Hmm how did you install Precise anyway (upgrade, fresh install, etc.)?

---

### Post by closbar on 2012-04-15
It was an upgrade from 11.10 but when I was updating the system crash  an now I`m stuck there

---

### Post by sotirisa on 2012-05-09
I also tried to upgrade to 12.04 from 11.10 and my system crashed during the upgrade. I could no longer boot, but then managed to fix that problem with a USB boot. 

Now I am still in 11.10 and the update manager only gives me the option for partial upgrade. When I run partial upgrade I also get:

[COLOR=Black]CAN NOT UPGRADE
an upgrade from `precise`to `oneiric` is not supported with this tool
[/COLOR]
The sudo apt-get upgrade command responds with 556 packages not upgraded. 

Please help.

---

### Post by drmrgd on 2012-05-09
You could try the old standby method of:

```
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
```

Which may help you fix the broken packages and dependency issues. Give it a shot and report back what happens.

---

### Post by sotirisa on 2012-05-11
sudo apt-get update and sudo apt-get upgrade seem to have done the trick. My system seems to be running 12.04 fine now.

---

### Post by taddygrrr on 2012-05-11
Been happy with ubuntu since 8.x.  Upgrading 11.10 -> 12.04 crashed with 4 minutes left, saying my system is likely in an unstable state.  After reboot, install is hosed.  If you have any doubts about upgrading, I'd recommend not to take upgrade until problems are acknowledged and fixed.

---

