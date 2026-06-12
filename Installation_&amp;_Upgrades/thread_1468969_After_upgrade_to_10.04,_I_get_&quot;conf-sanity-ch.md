---
title: "After upgrade to 10.04, I get &quot;conf-sanity-check-2 exited with status 256&quot; on log in"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Mothinator on 2010-05-01
I just upgraded to 10.04 from 9.10, and now whenever I log in I get the message: 

```

There is a problem with the configuration server.
(/usr/lib/libconf-2-4/gconf-sanity-check-2 exited with status 256)

```

After clicking "close", log in proceeds as normal.

I've tried all of the suggestions mentioned in [bug#383461]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/383461").

Namely, /etc/gconf/gconf.xml.system is chmodded to 755 and /tmp is chmodded 1777.

I also tried deleting ~/.gconf.

Running /usr/lib/libconf-2-4/gconf-sanity-check-2 from the terminal gives no output and exits with code 0.

Attached is my .xsession-errors.

Any help is appreciated. Thanks!

---

### Post by Mothinator on 2010-05-08
Reported as [Bug #577545]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545") on launchpad.

---

### Post by wkulecz on 2010-05-08
I get it but I'm stuck in an infinite long in loop when I click OK.

Virgin 10.04 install, installed the first round of updates this morning.  Guess I should have checked here first :(

How to fix?

On a hunch, Since I had added a drive to mount as /tmp on boot, I removed it and rebooted and things came up OK after skipping it in the bootup mount error prompt.  

I thought /tmp was not supposed to store state or data across restarts.  I know in the old days of tight disk space, rm -rf /tmp/* was a common command in the startup scripts.

---

### Post by Mothinator on 2010-05-08
Some say that you need to chmod /tmp 1777. Mine is already set that way, so this was not my problem, but maybe it'll help you.

---

