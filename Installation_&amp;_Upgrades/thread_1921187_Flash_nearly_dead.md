---
title: "Flash nearly dead"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by vcell on 2012-02-06
Flash was working fine on my 32 bit system, until my wife hit "Install Updates". Suddenly sites that normally played Flash fine, say we need to update. However YouTube works fine in HTML5 and the flash test at Adobe's site also works. But game sites, Facebook games, HULU, etc. either recommend installing flash or just do not operate.

According to Adobe, Flash Player 10,1,999,0 is installed, but Flash Player 11.1.102.55 is recommended. When attempting to upgrade to 11, the Adobe site redirects to the Ubuntu Software Center, which shows the Flash Player 10 plugin installed, and nothing for 11 available.

Has anyone else experienced this problem?

---

### Post by darkod on 2012-02-06
What I tend to do for Flash ever since my first ubuntu install (version 9.10) is to download it from Adobe website (not upgrade, download as if you don't have it), not use the downloaded file to install but instead simply extract the file where ever you want.

From the extracted folder just copy the library, which name was something like lib-something.so and paste it into Home/.mozilla/plugins or Home/.mozilla/firefox/plugins.

When I get home I can give you the exact library name and the folder destination. I don't have them right now at work.

I used this initially for 64bit because it was a big hassle to get 64bit working back then, but even today I kept using the same method. Much better then installing, upgrading, etc. In reality it only needs the library copied into the plugins folder.

---

### Post by Linux Dutchman on 2012-02-06
What you also can do is downloading and install the Flash-aid plugin for firefox. This plugin checks/download/remove/install Flash driver(s).
 
Check: which version of Ubuntu you're running (32-bit or 64-bit)
Remove: it removes any conflicting flahsh drivers
download/install: Getting the correct version on your system!

---

### Post by Frogs Hair on 2012-02-06
Script blocking software may be the cause of an flash out date message . You may have to reset page permissions .

I have also gone with Flash Aid and install flash via Firefox , which automatically downloads from the Adobe site .

There is no longer need to update flash via the update manger because Flash Aid displays the update notification long before anything appears in the update manager .

---

