---
title: "Upgrade 12.04 LTS to 14.04 LTS"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by bardu on 2014-07-30
Is there still no upgrade from 12.04 LTS to 14.04 LTS available?

---

### Post by TheFu on 2014-07-30
I updated from 12.04.4 to 14.04 in June and again in July for a different machine.  I'm in the USA.  Different parts of the world get the update at different points based on their local repos, I hear.

You don't need to wait for the GUI to tell you this - you can force the 14.04 update (upgrade is a strong term).

---

### Post by Rob Sayer on 2014-07-31
I think the release update should be available in Canada, which is where I'm typing this from, though Nova Scotia is as far as you can get from the Yukon.

Myself I don't use the Canada server for updates.  I don't think it's quite as well maintained or as fast as the main server.  But it's hosted at the university of Waterloo, and they're no slouches.  I'd be *extremely* surprised if they didn't have the updates there.  I just found it slow sometimes, especially weekends.  Maybe their support goes downhill in the summer?

I changed the server setting in Synaptic package manager.  I don't know where that setting is in the update manager because I've just updated with the terminal for a while.  But it shouldn't be hard to find.

---

### Post by TheFu on 2014-07-31
> **Rob Sayer said:**
> I changed the server setting in Synaptic package manager.  I don't know where that setting is in the update manager because I've just updated with the terminal for a while.  But it shouldn't be hard to find.

/etc/apt/ is where those settings are.

I would do this:
Make a know-I-can-restore backup - 100% know I can restore, then:
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo do-release-upgrade
```
If any one of those steps fails, I would NOT continue before fixing the issue.

---

### Post by bardu on 2014-07-31
Yeah, I got the 12.04 release from the Waterloo server. Unfortunetaly, this is my dev machine and due to workload I can't afford playing around and ending up with a mess. Guess I have to wait ...

---

