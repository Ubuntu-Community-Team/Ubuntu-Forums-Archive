---
title: "Upgrade to Hardy, Eclipse BIRT not working"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by ghetto2ivy on 2008-04-28
Title says it. I upgraded my Machine to Hardy from gutsy, and now Eclipse's BIRT plugin doesn't work. I tried using the version in the repo & using the install plugin feature to add birt, but no dice... it still refuses to load a reports.

Error log barks about BIRT not being installed  and about Jface not initializing. Even from a fresh all-in-one download.

Anyone else seeing this? Solutions?

---

### Post by ghetto2ivy on 2008-05-06
No one else uses BIRT on Ubuntu? I'm seeing this error even on VM fresh installs. No tips on how to diagnose? No other related Eclipse errors?

---

### Post by ghetto2ivy on 2008-05-16
Solution: Upgrade to BIRT 2.3.0

BIRT used firefox in the backend, that was broken with the upgrade to firefox3

---

### Post by jbaruch on 2009-04-27
Hi, Steven!

Did you solve your ["Invalid javascript expression: dataSetRow"]("http://www.eclipse.org/newsportal/article.php?id=32329&group=eclipse.birt") problem?
I encounter the same problem, and there is no valuable information over the net. Eclipse's "News-Portal" can't track responses, so I don't know how did you manage.

Thanks in advance,
Baruch.

---

### Post by jbaruch on 2009-04-27
OK, finally found it:
[http://www.eclipse.org/newsportal/article.php?id=32368&group=eclipse.birt](http://www.eclipse.org/newsportal/article.php?id=32368&group=eclipse.birt)
Birt doesn't work with open-jdk, and there is no single word about it anywhere in Birt documentation. I found this amazing.

---

### Post by ghetto2ivy on 2009-04-29
Yes, its worked fine since the switch to sun java. I'd think its more of a openJDK compliance issue than a Birt issue. Eclipse is pretty respectable when it comes to java apps.

---

