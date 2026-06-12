---
title: "hello, new versions Firefox 8.0 and Thunderbird Mail 8.0 is about 4-5 days..."
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-11-14
hello, new versions Firefox 8.0 and Thunderbird Mail 8.0 is about 4-5 days, how can I install, because &quot;Software Up to Date&quot; cannot installing, I wait for your answer, thanks a lot...

---

### Post by fantab on 2011-11-14
> **spi_ said:**
> hello, new versions Firefox 8.0 and Thunderbird Mail 8.0 is about 4-5 days, how can I install, because &quot;Software Up to Date&quot; cannot installing, I wait for your answer, thanks a lot...

If you want Latest versions of Mozilla then:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable 

sudo apt-get update 

sudo apt-get upgrade
```

You may be warned at the time of adding the repository that its for 10.04 but, I guess, its safe to add them.

---

### Post by subehsharma on 2011-11-14
As Ubuntu 11.10 comes with Thunderbird & Firefox by default, there is no need for a PPA. Thunderbird 8 & Firefox 8 will be available in the official Oneiric repositories soon and then you can simply use Update Manager to upgrade them.

You can keep an eye on the availability of Thunderbird 8 by visiting this page:

[http://packages.ubuntu.com/search?ke...ic&section=all](http://packages.ubuntu.com/search?ke...ic&section=all)

Notice, it states "7.0.1+build1+nobinonly-0ubuntu1: amd64 i386" currently.

---

### Post by fantab on 2011-11-14
> **subehsharma said:**
> As Ubuntu 11.10 comes with Thunderbird & Firefox by default, there is no need for a PPA. Thunderbird 8 & Firefox 8 will be available in the official Oneiric repositories soon and then you can simply use Update Manager to upgrade them.

You can keep an eye on the availability of Thunderbird 8 by visiting this page:

[http://packages.ubuntu.com/search?ke...ic&section=all](http://packages.ubuntu.com/search?ke...ic&section=all)

Notice, it states "7.0.1+build1+nobinonly-0ubuntu1: amd64 i386" currently.

Yes they will be... but the above ppa is the latest stable-releases from Mozilla with the latest fixes... this does not happen fast enough on ubuntu.

---

### Post by lovinglinux on 2011-11-15
See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

