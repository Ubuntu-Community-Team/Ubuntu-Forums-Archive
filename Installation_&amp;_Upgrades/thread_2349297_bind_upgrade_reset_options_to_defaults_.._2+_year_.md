---
title: "bind upgrade reset options to defaults .. 2+ year open bug ... please fix"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by heldal2 on 2017-01-13
It's been known for a couple of years that bind as integrated with systemd does not use the configuration from /etc/default/bind9. This poses a problem in particular for bind-users who do not have IPv6-connectivity. Most, if not all, hints on how to prevent bind from using ipv6 tells the user to edit /etc/default/bind9, but that will have no effect. The bind-package include an options-file for systemd (/lib/systemd/system/bind9.service), but options added to this file are reset with every upgrade of bind. I just got a confirmation that this hasn't yet been fixed when the last security-upgrade to bind on xenial was installed.

The solution suggested to bind-developers in order to maintain backwards compatibility in the best way possible is to include the defaults-file from the systemd service file. I.e. modify /lib/systemd/system/bind9.service so that /etc/default/bind9 is included with a service section like this:

```
[Service]
EnvironmentFile=-/etc/default/bind9
ExecStart=/usr/sbin/named -f $OPTIONS
ExecReload=/usr/sbin/rndc reload
ExecStop=/usr/sbin/rndc stop
```

This has been going on for an embarrassingly long time (2+ years), but should finally have been fixed in the head-branch of bind in late december 2016. Could someone also please push this fix for bind9 to the various branches in the ubuntu-universe that use systemd.

---

### Post by ian-weisser on 2017-01-13
You can make this happen with a few minutes of research and a bit of persistence.

Debian Maintainers and Ubuntu Developers get deluged with messages every day, far more then they can possibly address. The way for you to cut through the noise is to make it obvious that you have done your homework, and make it super-easy for the Debian Maintainer and the Ubuntu Developer(s) to implement the fix and close the bug.

1) Please locate the appropriate Launchpad bug, the appropriate Debian bug, and the appropriate (fixed) upstream bug report. Connect all three.
2) Then e-mail the Debian maintainer, pointing them the the Debian and upstream bugs.
3) After Debian has successfully rebuilt the package with the fix, then e-mail the Ubuntu maintainer, pointing them to all three bugs, and that Debian has just implemented a fix.
4) After the bug is Fix Released in Ubuntu, request an SRU or backport if desired for older releases of Ubuntu.

---

