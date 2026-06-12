---
title: "How can I correct a 4800: PyGIWarning"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2016-10-21
Received the following message as I was installing  Boot-repair? Whatever I found on the web is meaningless with my knowledge level, hope someone here can shed light on this and how to correct it. Xubuntu 16.04, 64bit.

> 
~$ /usr/bin/glade2script:4800: PyGIWarning: Notify was imported without specifying a version first. Use gi.require_version('Notify', '0.7') before import to ensure that the right version gets loaded.
  from gi.repository import Notify
/usr/bin/glade2script:4804: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator


---

### Post by CantankRus on 2016-10-22
Are you installing from the [**_[COLOR="#B22222"]boot-repair ppa[/COLOR]_**]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair")?
According to this [**_[COLOR="#B22222"]bug[/COLOR]_**]("https://bugs.launchpad.net/boot-repair/+bug/1573302") it has been fixed in the glade2script package from the ppa.

---

### Post by ineuw on 2016-10-22
> **CantankRus said:**
> Are you installing from the [**_[COLOR="#B22222"]boot-repair ppa[/COLOR]_**]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair")?
According to this [**_[COLOR="#B22222"]bug[/COLOR]_**]("https://bugs.launchpad.net/boot-repair/+bug/1573302") it has been fixed in the glade2script package from the ppa.

CantankRus, thanks for the info. It was an accurate guess. How would I know which package has been fixed? I am using Xu 16.04 64bit and the PPA.

---

### Post by CantankRus on 2016-10-22
Make sure the ppa is enabled and...
```
sudo apt update
sudo apt upgrade  
```

Then check....
```
apt policy glade2script boot-repair
```
eg
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt policy glade2script boot-repair**
glade2script:
  Installed: 3.2.3~ppa1
  Candidate: 3.2.3~ppa1
  Version table:
 *** 3.2.3~ppa1 500
        500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status

boot-repair:
  Installed: 4ppa38
  Candidate: 4ppa38
  Version table:
 *** 4ppa38 500
        500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by ineuw on 2016-10-22
CantankRus, again my thanks. The output was identical to the above and boot repair works fine.

---

