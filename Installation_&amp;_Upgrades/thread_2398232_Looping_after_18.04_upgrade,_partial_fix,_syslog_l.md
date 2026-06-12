---
title: "Looping after 18.04 upgrade, partial fix, syslog loop with ayatana"
date: 2018-08-09
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2018-08-09
I am fighting a problem with very bad performance after 18.04.1 upgrade
I have 2 desktops, one is fine and one is not.

Initially I tracked the problem to Baloo.
I was unable to use the looping PC (well, I could, but it would take 50 times as long) but I can use the other one to do research.
I found that Baloo indexer was a major problem for KDE users, but I'm using vanilla Ubuntu.
I tried for a while to disable Baloo, but no luck.
I looked at the syslog and found a growing file.
Then I uninstalled all KDE apps that I had - still no good.
Then I happened to see complaints from Mate users about Baloo.
So I uninstalled all Mate apps.
Now at least I can use this PC again.

But the growing Syslog file is worrying:

```


Aug  9 10:39:39 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:39 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
Aug  9 10:39:39 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:39 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
Aug  9 10:39:39 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead
Aug  9 10:39:40 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Item :1.66/org/ayatana/NotificationItem/multiload is already registered
Aug  9 10:39:41 Arctic gnome-shell[1806]: [AppIndicatorSupport-WARN] Attempting to re-register :1.66/org/ayatana/NotificationItem/multiload; resetting instead

```

Any idea what is happening?

Thanks for you help.

---

### Post by Claus7 on 2018-08-10
Hello,

I would like just to offer some minor input. Checking the information you are providing to my ubu box, I can see that jayatana is installed. Under /var/log/syslog I do not find anything that has to do with ayatana. Maybe checking synaptic, see if you have more ayatana-like packages installed that are causing this issue and can be removed or just re-install that jayatana package.

Regards!

---

### Post by hans12345 on 2018-08-24
I have searched with ayatana in the synaptics search.
Initially I just removed anything with ayatana in the description. No effect on my growing syslog.
Then I removed anything that showed up as related to ayatana in synaptics. This meant removing all Unity stuff.
But still my syslog grows:

```

Aug 24 11:14:14 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:14 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:14 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:14 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:15 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:16 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead
Aug 24 11:14:16 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Item :1.60/org/ayatana/NotificationItem/multiload is already registered
Aug 24 11:14:16 Arctic gnome-shell[2003]: [AppIndicatorSupport-WARN] Attempting to re-register :1.60/org/ayatana/NotificationItem/multiload; resetting instead

```

How do I stop this registering?

Advice please !

---

### Post by Claus7 on 2018-08-24
Hello,

it seems to be a bug: [https://bugs.launchpad.net/ubuntu/+source/indicator-multiload/+bug/1768127](https://bugs.launchpad.net/ubuntu/+source/indicator-multiload/+bug/1768127)

why don't you get rid of indicator-multiload package?

Regards!

---

### Post by larry-opendoorworld on 2018-08-25
i had the same system log "[COLOR=#333333][FONT=Menlo]jayatana" [/FONT][/COLOR]error.... 
here is what stopped it... 

sudo apt-get remove indicator-multiload


improvements welcome.... :-)

---

### Post by hans12345 on 2018-08-26
If I  remove indicator-multiload, I loose lots. This is what synaptic package manager says it does:

Graphical system load indicator for CPU, ram, etc.
A system load indicator capable of displaying graphs for CPU, ram, and swap
space use, plus network traffic.

---

### Post by Claus7 on 2018-08-27
Hello,

> **hans12345 said:**
> If I  remove indicator-multiload, I loose lots. This is what synaptic package manager says it does:

Graphical system load indicator for CPU, ram, etc.
A system load indicator capable of displaying graphs for CPU, ram, and swap
space use, plus network traffic.

in Lubuntu 18.04 is not installed by default. You can still have access to ram, cpu and disk storage without using this package. You could test it as well by removing it and checking if you are still getting the growing syslog file. I would suggest a complete removal and then re-installation.

Regards!

---

