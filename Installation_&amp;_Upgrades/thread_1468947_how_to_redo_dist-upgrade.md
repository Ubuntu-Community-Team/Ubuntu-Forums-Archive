---
title: "how to redo dist-upgrade?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by jangirke on 2010-05-01
Hi How do I redo a dist-upgrade? Looks like I broke something during upgrade and now I don't want to restart until I forced the upgrade routine to run a second time.

---

### Post by snowpine on 2010-05-01
If I am understanding your question correctly, why not just:

```
sudo apt-get dist-upgrade
```

a second time? It should pick up right where you left off. At the minimum it should provide useful error messages. 

If you want to be more specific about what you tried and what it broke, maybe you'll get better advice. :)

---

### Post by garvinrick4 on 2010-05-01
If anything is broken just Code:

sudo apt-get -f install

sudo apt-get clean

sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get -f install

Should not have anything broken after this.

---

