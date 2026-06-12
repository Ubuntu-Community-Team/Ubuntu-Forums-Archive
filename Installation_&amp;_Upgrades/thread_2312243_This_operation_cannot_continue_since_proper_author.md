---
title: "This operation cannot continue since proper authorization was not provided"
date: 2016-02-03
forum: Installation &amp; Upgrades
---

### Post by oygle on 2016-02-03
Muon update manager keeps on giving this message - "This operation cannot continue since proper authorization was not provided"

I had this problem in Oct 2014, so did the same fix ..

```
sudo apt-get update

sudo apt-get upgrade
```

Is it a bug ? Even if I try to run the update manager after the above code, I still get the same error message.

---

### Post by Vladlenin5000 on 2016-02-03
A bug perhaps but most likely you have other issues with broken/held packages...

According to this you need **polkit-kde-1** in order to have Muon ask for elevated privileges. So, before anything else, try:
```
sudo apt-get install --reinstall polkit-kde-1
```

If the system persists then do
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
In order to have your system fully updated. If you notice any error message after any of the aforementioned commands please post the complete message.

---

