---
title: "mythtv-backend not starting on boot"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by madverb on 2009-11-30
Since upgrading to Karmic mythtv's backend has failed to start on boot.
I'm not sure if it only new that mythtv-backend is using upstart. Is it possible that the upstart setup is causing problems.

```
# MythTV Backend service

description     "MythTV Backend"
author          "Matt Mossholder <matt@mossholder.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [016]

#expect fork
respawn

script  
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script

```

I'm also not getting any errors in /var/log/boot

---

### Post by madverb on 2009-12-01
Bump!

---

### Post by madverb on 2009-12-01
Nevermind. I think that the default upstart script is wrong.

net-device-up doesn't seem to work. I have just changed it to net-device-added.
Now it works fine.

---

