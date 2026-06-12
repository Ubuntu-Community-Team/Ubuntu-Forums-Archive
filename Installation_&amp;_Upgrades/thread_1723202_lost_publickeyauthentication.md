---
title: "lost publickeyauthentication"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by lister king of smeg on 2011-04-06
Hi i have accidently deleted my public keys. first the update manager started throughing errors, now synaptic, apt, and ubuntu Software center are all throughing errors at me i need help. I am using vanilla Ubuntu 10.04LTS AMD64.

---

### Post by tommcd on 2011-04-06
From Synaptic select: settings > repositories. On the authentication tab, select "Restore Defaults". Then see if you can update:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by lister king of smeg on 2011-04-06
thankyou my computer was realy tweaking out after only getting about one out every three updates, for several months.

---

