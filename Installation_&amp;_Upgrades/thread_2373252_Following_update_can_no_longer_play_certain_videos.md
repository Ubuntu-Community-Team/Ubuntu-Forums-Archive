---
title: "Following update can no longer play certain videos"
date: 2017-10-04
forum: Installation &amp; Upgrades
---

### Post by RegUB on 2017-10-04
This morning I installed the following Ubuntu updates -
```
cat /var/log/apt/history.log

Start-Date: 2017-10-04  10:13:53
Commandline: aptdaemon role='role-commit-packages' sender=':1.91'
Upgrade: firefox-locale-en:amd64 (55.0.2+build1-0ubuntu0.14.04.1, 56.0+build6-0ubuntu0.14.04.1), firefox:amd64 (55.0.2+build1-0ubuntu0.14.04.1, 56.0+build6-0ubuntu0.14.04.1), libidn11:amd64 (1.28-1ubuntu2.1, 1.28-1ubuntu2.2), libpoppler-glib8:amd64 (0.24.5-2ubuntu4.5, 0.24.5-2ubuntu4.6), libpoppler44:amd64 (0.24.5-2ubuntu4.5, 0.24.5-2ubuntu4.6), libnss3-nssdb:amd64 (3.28.4-0ubuntu0.14.04.2, 3.28.4-0ubuntu0.14.04.3), dnsmasq-base:amd64 (2.68-1ubuntu0.1, 2.68-1ubuntu0.2), ca-certificates:amd64 (20160104ubuntu0.14.04.1, 20170717~14.04.1), libnss3:amd64 (3.28.4-0ubuntu0.14.04.2, 3.28.4-0ubuntu0.14.04.3), poppler-utils:amd64 (0.24.5-2ubuntu4.5, 0.24.5-2ubuntu4.6)
End-Date: 2017-10-04  10:15:29

```

Following this I can no longer play BBC weather videos ([http://www.bbc.co.uk/weather/]("http://www.bbc.co.uk/weather/")) - I get a message saying "Sorry, you need Flash to play this". This was working fine immediately before the upgrade.

Initially I thought it was a Firefox issue, as a new Firefox update is included in the list above. But I am getting the same problem in Chrome. Is there something else among the updated software that could be to blame?

---

### Post by ajgreeny on 2017-10-04
Same here for me in the UK, as you appear to be. I don't have Chrome but the problem is also in chromium.

BBC-iPlayer works fine for me, but that is now set on my machine to use html5 not flash, so I'm not sure if flash would also be a problem for that site.
Are you still on 14.04 as I am using 16.04, and Xubuntu, not Ubuntu, though that should not make any difference.
I have adobe-flashplugin installed from the canonical-partner repos, and that is now version 27.0r0.

The BBC does it again, it seems, though I have no way to check if this site works on Windows or other OSs apart from a VM of WinXP in VBox where the problem is precisely the same, so this problem is probably nothing to do with us using Ubuntu but some change to BBC settings of some sort.

Watch this space I think....?

---

### Post by Autodave on 2017-10-04
Just found this out a few minutes ago: Firefox 53 and above no longer supports Java (and evidently Flash).  Found this out on Firfox's website.

---

### Post by Autodave on 2017-10-04
Midori seems to work OK.

---

### Post by RegUB on 2017-10-04
Yes, still using 14.04. It worked this morning immediately before I installed the upgrade, so if it is a BBC change then it's a big coincidence!

---

### Post by ajgreeny on 2017-10-04
> **Autodave said:**
> Just found this out a few minutes ago: Firefox 53 and above no longer supports Java (and evidently Flash).  Found this out on Firefox's website.
I don't think that java is directly related as flash worked in FF55, as RegUB says.

However, the adobe flash site at [http://get.adobe.com/flashplayer/about/](http://get.adobe.com/flashplayer/about/) now just shows a completely empty space where it used to show a bouncing red flash cube in all previous FF versions.  That site does still work in chromium, so it is something different about both the BBC weather site which will not work in either browser, and FF56 which will not show flash videos at all.

---

### Post by RegUB on 2017-10-05
Another Firefox update this morning (56.0) has fixed the problem!

---

### Post by Autodave on 2017-10-05
Just did the update and mine is working again, too.

---

### Post by ajgreeny on 2017-10-05
Same here; all good again for those few sites that still demand flash.

---

