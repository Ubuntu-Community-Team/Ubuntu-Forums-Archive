---
title: "hello, why I see always this message:"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2011-11-24
hello, why I see always this message: 

***&#8220;Failed to download repository information   Check your Internet connection. W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found  , W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found  , E:Some index files failed to download. They have been ignored, or old ones used instead.&#8221; ***

while the Firefox updated successfully and all updates updated successfully?  how to I remove this message?

---

### Post by oldos2er on 2011-11-24
There's no oneiric repository there, it only goes up to natty.

Run ```
gksu software-properties-gtk
``` and remove the PPA under the Other Software tab.

---

### Post by darkod on 2011-11-24
If your internet connection is running fine, it might be a problem with the repository. Go into Software Sources and look around. If you have added any manual repositories try disabling them. They might not be online any more.

---

