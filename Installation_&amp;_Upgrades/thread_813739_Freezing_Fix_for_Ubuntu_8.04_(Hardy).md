---
title: "Freezing Fix for Ubuntu 8.04 (Hardy)"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by sudo panda on 2008-05-31
Hi Everyone!
Just in case someone has had the same problems as i have with the newest distribution of Ubuntu.
When i first installed it i found that i would experience random lock ups/freezes landing me with no mouse movement and the keyboard lights flashing. **the only way out was to do a hard restart**

Well, after much troubleshooting and grumbling i finally worked out what was wrong (with mine anyway).
Someone else had the same issue and fixed it via this method in a post on this thread: [http://ubuntuforums.org/showthread.php?t=587905&page=65]("http://ubuntuforums.org/showthread.php?t=587905&page=65")

I currently use a rt61 wireless card, and after recording my system a few moments before a lock up using this post: [http://ubuntuforums.org/showthread.php?t=587905&page=64]("http://ubuntuforums.org/showthread.php?t=587905&page=64")

I worked out that it was in fact the Network Manager that comes with the ubuntu system stuffing my system around.

So i simply uninstalled Network Manager with the Synaptic Manager and haven't had a freeze yet :)
Unfortunetly that landed me with no internet connection, however i just went back to using Rutilt Wlan Manager as that worked well for me in 7.10.
(i had to reinstall my rt61 driver however)

Just noting this down for anyone that might be stuck like i was. 

Cheers.

---

