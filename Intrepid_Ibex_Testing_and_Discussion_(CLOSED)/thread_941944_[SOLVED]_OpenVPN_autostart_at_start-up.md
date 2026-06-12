---
title: "[SOLVED] OpenVPN autostart at start-up"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Piraja on 2008-10-08
Dear all,

I think I originally misplaced a thread whose proper place would have been here:
[http://ubuntuforums.org/showthread.php?t=919715](http://ubuntuforums.org/showthread.php?t=919715)
To save you the trouble of reading that previous thread, let me recapitulate: If I have OpenVPN autostart enabled, I'm prompted at start-up time to give my VPN username and password. This is not what I want and I suppose this is not how it should be &#8212; in any case, this did not happen with Hardy.

Any knowledgeable suggestions would be appreciated! In any case, I think the next stop is [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/openvpn/+bug/280428")...

---

### Post by Piraja on 2008-10-10
Thanks to Thierry Carrez for the solutions offered at [Launchpad]("https://answers.launchpad.net/ubuntu/+source/openvpn/+question/47501"). Special thanks for his consideration of changing the VPN autostart behavior in Intrepid, with reference to the correspondent behavior in Hardy.

**P.S. (edit)** As my desktop PC still runs Hardy, I just noticed that OpenVPN is autostarted in a similar manner in Hardy, except that instead of halting at the username prompt, the boot-up continues after an automatic failure of authentication ("Auth username: (FAILED)"). That's better!

---

