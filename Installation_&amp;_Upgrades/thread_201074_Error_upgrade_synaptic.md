---
title: "Error upgrade synaptic"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by hindrik on 2006-06-21
Hell I've made so I'm not able to update with synaptic I tried to add a repository a new and not suported one and the result was that I cant update att all. The fault message is as follows:
E: Typ "http://packages.freecontrib.org/ubuntu/plf/" är okänd på rad 22 i listan över källor /etc/apt/sources.list
E: Källistan kunde inte läsas.
Gå till förrådsdialogen för att rätta till problemet.

Unknown message at line 22 over sources and it says got to the dialog for repositories and change it! I have tried but the problem still remain how can I remove this line in the source list?
I would be grategul if someone could help me.
Regards Hindrik:confused:

---

### Post by rcarring on 2006-06-21
```

cd /etc/apt/
ls
sudo cp sources.list sources.list.old
sudo nano sources.list
----look for the offending line and comment it out using a #----
---- to save amended file do crtl-o
---- then ctrl-x to exit

```

---

