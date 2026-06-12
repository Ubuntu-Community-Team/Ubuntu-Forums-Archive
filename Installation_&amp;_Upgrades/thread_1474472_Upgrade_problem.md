---
title: "Upgrade problem"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by csshreeram on 2010-05-06
Hello Everyone

I was so impressed by the screen-shots of 10.04 LTS that i wanted upgrade via the update manager( am using karmic 9.10).Everything went well with downloading the new packages till the point of installation of downloaded packages.Halfway through the installation power went off and when i restarted the system it was stuck at some point with the message 
```
mount:nothing to mount in /dev
``` or something like that.Then i restarted the system in recovery mode and ran "dpkg" to fix broken packages hoping it would fix the issue.It did to some extent that i was type the problem here through the affected system.

The problem is i couldn't send the crash report the first time around and i can't get hold of it now.My system is somewhere between karmic and lucid ("About Ubuntu" shows as karmic and System Monitor shows it as lucid").So i how do i get a clean installation of lucid?

help me out

TIA
C.S.Shreeram

---

### Post by kansasnoob on 2010-05-06
So you can login to the desktop? If so run:

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

Those could even be run after selecting "netroot" from Recovery Mode.

---

### Post by csshreeram on 2010-05-06
:popcorn:woohoo

That worked like a charm.Now fingers crossed,will upgrade my hardy laptop also.One annoying thing is the so many versions on the grub every time a update is done.Are they all necessary? if not how can i get rid of them and keep the latest one alone.Thnx(should i start a new thread for this?)


Thanks again

Shreeram

---

