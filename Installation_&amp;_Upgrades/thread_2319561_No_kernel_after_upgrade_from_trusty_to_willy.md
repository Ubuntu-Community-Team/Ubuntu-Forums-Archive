---
title: "No kernel after upgrade from trusty to willy"
date: 2016-04-05
forum: Installation &amp; Upgrades
---

### Post by firelmnt on 2016-04-05
Hello guys,

I'm currently facing some huge problems with upgrading Ubuntu.
This happened twice already.

So, after using LTS version for some time I thought of upgrading to the latest available version (willy) and normally started upgrade process (in graphical way).
After fetching all packages and some time of applying changes, screen went black. I thought it's been restarting or screen saver was activated (even though I have it disabled) but staying still for next half an hour or so, I tried to at least switch to console mode but couldn't do a thing by pressing any key combination I know, only hard shutdown helped (pressing and holding power key). After rebooting I got only to console mode and could resume applying changes by typing ```
dpkg --reconfigure -a
```. After success I rebooted and in grub menu there wasn't any Ubuntu nor Advanced Options item.

I have tried looking to /boot directory and there is no kernel image except memorytest.
I have already tried chrooting but couldn't run sudo.

Any idea? If it would be possible not to do a clean install, I would appreciate.

---

