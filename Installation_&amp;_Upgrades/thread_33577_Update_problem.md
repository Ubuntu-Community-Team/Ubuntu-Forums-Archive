---
title: "Update problem"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by Genesius on 2005-05-11
Utter Ubuntu n00b here, so sorry if this is a dumb question, but I haven't been able to find it in the FAQs.

Got a dual-boot XP/Ubuntu, with XP on my master HD and Ubuntu on a secondary. Got installed correctly, but I get an icon that there are 12 updates available. When I click on it it asks for my password, I type it in, the window goes away and nothing happens. Tried running sudo apt-get updates, same thing - asks for my password and then nothing.

Any suggestions as to how I can get updaes to run?

---

### Post by defkewl on 2005-05-11
Try using synaptic. It in the administration menu if I'm not wrong.

---

### Post by Professor X on 2005-05-11
The manual way to upgrade is:

```
sudo apt-get update
sudo apt-get upgrade
``` 

Make sure your repositorie info. is correct.  The list of repositories is in  /etc/apt/sources.list.  [http://www.ubuntuguide.org](http://www.ubuntuguide.org) shows you which ones you want.

 Hope that helps.

---

