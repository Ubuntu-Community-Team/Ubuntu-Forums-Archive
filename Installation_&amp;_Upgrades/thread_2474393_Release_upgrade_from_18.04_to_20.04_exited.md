---
title: "Release upgrade from 18.04 to 20.04 exited"
date: 2022-04-28
forum: Installation &amp; Upgrades
---

### Post by ordak on 2022-04-28
Hi,

I was upgrading Ubuntu on a laptop. From 18.04 to 20.04 LTS to be precise. During "sudo do-release-upgrade" at one stage when I was asked to remove some extra packages , I decided to read the names of packages , So I sent "d". At the end of the list I made a mistake. Instead of pressing "esc" I pressed "ctrl+c". The whole upgrade was interrupted. I restarted the laptop and browsers and other software seem to work. My question is how can I finish the installation with some commands ?

Thanks.

---

### Post by ActionParsnip on 2022-04-28
Try:
```

sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```

If that is smooth, then rerun the upgrade. Personally I'd just wipe the install and do a clean install of Jammy, then restore user data from your backups.

---

