---
title: "fresh installed 10.10, now unable to boot!"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by geoffm on 2010-10-10
I just installed the 10.10 Desktop, formatting my / partition but keeping my /home, which is what I've always done for 2 years. I loaded the liveCD before I installed, it started fine. It installed without any error. I chose to download updates and install MP3 codecs. Great installer by the way.

However, Now when I try to boot Ubuntu, after a few seconds I get this dialog box:
> Could not locate ICEauthority file /home/geoff/.ICEauhority
I can only click Ok, then I get a second one:
> There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
I click Ok, then background loads then nothing. If I do Alt-F2 I get the normal launcher but I can't load apps.
Ctrl-Alt-Bckspace does nothing.
Ctrl-Alt-Del pops up the shutdown box and I can shutdown.

Thank god I could boot Windows. Now I'm in trouble though, I don't have any disk to install other Ubuntu versions, and I don't have room on my Windows HD to download one. Hopefully I can find a fix!

---

### Post by geoffm on 2010-10-10
I solved it.
Boot in recovery mode, root terminal.
```
chmod 1777 /tmp
chown -R geoff /home/geoff
```

I think the last line is overkill, but it worked anyway.

---

