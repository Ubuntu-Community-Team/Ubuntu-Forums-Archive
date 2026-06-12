---
title: "Evolution doesn't filter spam after upgrade"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by mimmo.marozzi on 2006-10-16
From about a couple of days, after the spamassassin upgrade i received from ubuntu repositories, evolution stopped to filter spam mails. Has anyone a fix for this problem?

---

### Post by tcarradine on 2006-10-23
for a quick fix you could remove SA 3.1.3 and roll back to 3.1.0a (in Synaptic that's "Package" - "Force Version" to select an older version than the most current to reinstall). 

This will get your spam filtered again until another update is released.

Tim

---

### Post by mimmo.marozzi on 2006-10-24
Thanks a lot! Going back to previous version of Spamassassin with your method solved the problem.

---

