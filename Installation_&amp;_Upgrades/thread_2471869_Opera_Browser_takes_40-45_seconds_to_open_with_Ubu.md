---
title: "Opera Browser takes 40-45 seconds to open with Ubuntu 20.04 LTS"
date: 2022-02-11
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2022-02-11
Recently installed Ubuntu 20.04LTS. Added a few programs and such and Opera Version:83.0.4254.27 that is up to date.

Boot up 20.04 and when first opening, Opera it is very slow to open, taking 40-45 seconds! Once it opens Opera runs fine. When I close it and relaunch, Opera opens in a couple seconds with no problems.
Chromium and Firefox open in about 5 seconds for me.

I still have up to date Opera on another SSD running Ubuntu 18.04 and Opera launches in 5-10 seconds on that system.
Strange that up to date Opera takes 40-45 seconds to launch with Ubuntu 20.04 on a new SSD just installed!

Question is why does it take so long to launch on first launch when powering up?
Is there some way to speed up this Opera launch?

Posted this in the Opera Help Forums but so far there has been no help or remedy given.

---

### Post by tea for one on 2022-02-11
> **cybrsaylr said:**
> Recently installed Ubuntu 20.04LTS. Added a few programs and such and Opera Version:83.0.4254.27 that is up to date.
Boot up 20.04 and when first opening, Opera it is very slow to open, taking 40-45 seconds! Once it opens Opera runs fine. When I close it and relaunch, Opera opens in a couple seconds with no problems.
Chromium and Firefox open in about 5 seconds for me.

The version of Opera browser 83.0.4254.27 via Ubuntu software is a [COLOR="#0000FF"]snap[/COLOR] package.
You can double-check this with the terminal:-
```
snap list
```

Have a search of these forums and you will find many discussions about snap packages.
They generally always open slowly first time in a session, subsequent openings are quicker.

---

### Post by cybrsaylr on 2022-02-12
tea for one 

Yes the Opera version was installed via the snap package in terminal. 

Opera does have a chronic problem not not playing many video codecs almost every time Opera upgrades/updates. This is discussed often on Opera Forums. 
After Ubuntu 20.04LTS was installed I installed Opera via the Opera site and many videos would not play. 
Posted this on the Opera Forums and one suggestion to fix this was completely uninstall Opera, then put code: 'snap install opera' in terminal. 
Did that and all videos would play then with no issues. 

Guess that only downside now is it takes 40-45 seconds to launch Opera.

---

### Post by Frogs Hair on 2022-02-12
The Opera .deb is available from the official site.

---

