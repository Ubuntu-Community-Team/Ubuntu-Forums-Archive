---
title: "Odd Gutsy Update Manager problem..."
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by CharlieSummers on 2007-12-03
I'm having an odd Update Manager problem which has only manifest in the last week or so. I am notified when updates are available. I launch Update Manager, and it tells me what updates are available. But if I click the Install Updates problem, the manager window just sits with the spinning pointer for hours...I eventually have to kill the process (window close box is useless, but also doesn't trigger the "busy" dialog). I *think* it should be asking me for my user password, since it never does get around to that, it just goes into never-never land.

Understand, opening a root terminal and using apt-get to update/upgrade works just perfectly; the problem seems to be in the GUI Update Manager only. While apt-get is the obvious workaround, having update-notify alert me visually and then have to resort to a command line instead of clicking seems somehow...wrong - is there a way to safely remove/reinstall the GUI front-end without screwing around with apt-get itself? Is there anything that should cause Update Manager to hang on or before asking me for the password so it can continue? Any other thoughts on what might cause this one minor but annoying problem?

For those interested, a grep of ps shows the following processes:

```
 8764 ?        Sl     0:03 /usr/bin/python2.5 /usr/bin/update-manager
 9666 ?        S      0:00 gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 52428803 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpqVjFOW
15549 ?        S      1:58 gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 56623107 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpxofart
22721 ?        S      1:47 gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 54525955 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmpBN_HfY
29863 ?        S      2:17 gksu --desktop /usr/share/applications/update-manager.desktop -- /usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 60817411 --progress-str Please wait, this can take some time. --finish-str Update is complete --set-selections-file /tmp/tmp61wE5k
```

---

### Post by louieb on 2007-12-03
Kinda odd - sounds like some bits got twisted.
Just wondering if a reinstall of packages update-manager and update-manager-core would cure the problem. Also wondering if package gksu isn't the problem.

---

### Post by CharlieSummers on 2007-12-04
> **louieb said:**
> Kinda odd - sounds like some bits got twisted.
Just wondering if a reinstall of packages update-manager and update-manager-core would cure the problem.

That's the one! This line:

```
apt-get --reinstall install update-manager-core update-manager
```

...in a root terminal fixed the anomaly, and the GUI Update Manager now...er...updates. Much thanks!

---

