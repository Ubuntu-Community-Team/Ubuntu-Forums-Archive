---
title: "Package Manager won't forget proxy!"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by matt_is_rockin on 2008-11-01
Hi all,

I'm having problems with the adding and removing packages.

When at work, I use a proxy, so have a systemwide proxy (wwwproxy.hud.ac.uk) and also add it to Firefox. However, at home, I need to turn this off, which shouldn't be a problem, and isn't for the web, but when using the Add/Remove application it won't connect, giving me the error "Could not connect to wwwproxy.hud.ac.uk:3128".

Now I've turned it off in the System->Preferences->Network Proxy, (set to direct internet connection. I've also checked in gconfig-edit under system and httpproxy, which shows up blank. And also in System->Administration-?Synaptic Package Manager, the preferences under network are set to direct internet connection, and I've even deleted what was greyed out under the proxy.

Finally, I've also been to etc/environment after finding some thread about that, but there's no mention of a proxy there either.

Any help would be much appreciated!

Thanks,
Matt

---

### Post by matt_is_rockin on 2008-11-01
Solved - I managed to turn everything off and then when I did another restart it seems to be working now.

I might be doing this often though. I don't really understand these things, but am I asking too much for the systemwide proxy update to not need a restart?

Matt

---

