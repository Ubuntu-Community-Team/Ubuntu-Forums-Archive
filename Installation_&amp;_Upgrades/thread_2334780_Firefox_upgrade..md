---
title: "Firefox upgrade."
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-08-22
Why doesn't ubuntu 16.04 upgrade firefox to 48.01?

Henry

---

### Post by TheFu on 2016-08-22
Did you 
```
sudo apt update
sudo apt upgrade

```?

I only patch weekly, so won't see any FF updates until Saturday.

Assuming that you have done those things, there might be a PPA with the latest FF version direct from Mozilla's team.  It does take some time for the Canonical team to build and test important updates like FF.

---

### Post by Hewjr100 on 2016-08-22
Yes I just ran the update and upgrade, 7 upgraded, but not firefox.

Henry

---

### Post by TheFu on 2016-08-22
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) is all I can suggest.  

I'm happy to wait until the Canonical team decides a version is ready, but we all have different thresholds.  I also run all browsers in a **firejail** "container", which should limit any backlash due to security or bugs.

---

### Post by SeijiSensei on 2016-08-22
I use the PPA from Mozilla-Team: [https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next)

Firefox updated today to 49.0b5.

---

### Post by Hewjr100 on 2016-08-23
Sorry SeijiSensei, but I stopped using alphas and betas a long time ago.

Henry

---

### Post by mlan on 2016-08-25
Firefox 48.0.2 is out and Ubuntu is still on 48.0. It's a bad practice that Ubuntu delays updates of this sort, as there are known security vulnerabilities in the original version (48)

---

### Post by Impavidus on 2016-08-25
It seems that the bugs fixed in [Firefox 48.0.1]("https://www.mozilla.org/en-US/firefox/48.0.1/releasenotes/") and [Firefox 48.0.2]("https://www.mozilla.org/en-US/firefox/48.0.2/releasenotes/") are either not that important (site compatibility) or Windows only. 48.0.2 is irrelevant for Linux.

---

### Post by vasa1 on 2016-08-25
> **Impavidus said:**
> ... 48.0.2 is irrelevant for Linux.
+1

> 

    Fix a startup crash issue caused by Websense (Windows only) (Bug 1291738)
Source: [https://www.mozilla.org/en-US/firefox/48.0.2/releasenotes/](https://www.mozilla.org/en-US/firefox/48.0.2/releasenotes/)

---

