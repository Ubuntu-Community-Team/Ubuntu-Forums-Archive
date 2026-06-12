---
title: "Xubuntu Gutsy - update manager"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Madmanguruman on 2008-01-25
Did an install of Xubuntu Gutsy on a very modest PC (64MB, P-II) using the alternate install CD, mainly for educational purposes (with the intention of increasing the RAM size later).

Install went well, desktop working fine, Update Manager informed me of 95 or so updates that needed to be installed. Told it to go ahead and update, cursor went to busy, went out for a few hours. Came back, still in the same state. Cannot close Update Manager. Opened up Synaptic Package Manager, successfully downloaded and installed the updates in about 25 minutes.

Next day, more updates, same problem with Update Manager. Synaptic worked fine. Reinstall update-manager via Synaptic, haven't retried yet (will do so soon)

I'm just curious as to whether or not anyone has had similar issues with Update Manager.

---

### Post by taurus on 2008-01-25
Instead of using the Update Manager, see if you can do it from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Madmanguruman on 2008-01-25
Will do. Thanks.

---

