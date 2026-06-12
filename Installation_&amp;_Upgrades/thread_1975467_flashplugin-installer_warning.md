---
title: "flashplugin-installer warning"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by Jackie999 on 2012-05-07
I followed some threads here and removed flashplugin-installer from synaptic and moved an older version to ~/.mozilla/plugins
When I go to adobe site (in FF) it shows "You have version 11,1,102,63 installed"
Every restart I'm getting a warning "The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed...flashplugin-installer "
Any way to disable the alert?

---

### Post by Jackie999 on 2012-05-07
Found my answer [ here ]("http://www.kubuntuforums.net/showthread.php?58340-Yellow-light-bulb-icon-Bug-light")


```
sudo rm /var/lib/update-notifier/user.d/data-downloads-failed
sudo rm /var/lib/update-notifier/user.d/data-downloads-failed-permanently
```

---

### Post by mErchamion on 2012-11-28
thankyou, that popup was driving me crazy.

---

