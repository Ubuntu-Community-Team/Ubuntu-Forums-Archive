---
title: "problem after installing pepper-flash"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by 4dr14n on 2014-06-12
Hello all,

Few minutes ago, I installed pepper-flashplugin after recommendation from Chromium, the idea was to be able to run correctly flash stuff on the browser. Actually, I don't see the difference and flash videos (like youtube) still have the same problems than before (I got used to watch them from Minitube instead of from the browser, cause from that program I can watch them perfectly). 
Ah, I am working on Lubuntu 14.04 from yesterday (I had 13.10).
Now I have one more problem and it's that I cannot write using Chromium, when I type, it doesn't work. At the moment I am writing from Firefox, but I'd like to know how to solve the problem and/or if you recommend me to uninstall the pepper-flash package or not... 

Thanks a lot for your help.

---

### Post by bapoumba on 2014-06-12
You need to have the multiverse repositories enabled and install the package pepperflashplugin-nonfree : [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)
Then run the installer.

For Chromium, there is a bug, you need to run **ibus exit** at each login : [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)
From the last messages, looks there will be a fix. Some have removed ibus to fix the issue, but I'd rather keep it to test the new package.

---

