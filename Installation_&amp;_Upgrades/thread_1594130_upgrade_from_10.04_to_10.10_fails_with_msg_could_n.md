---
title: "upgrade from 10.04 to 10.10 fails with msg could not calculate the upgrade"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-10-12
I was updating from 10.04 to 10.10 (was updating through update manager))
after some time I got following message


```

An unresolvable problem occurred while calculating the upgrade:
E:Unable to correct problems, you have held broken packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the
'update-manager' package and include the files in
/var/log/dist-upgrade/ in the bug report.

```

When I tried to run the command 
```

ubuntu-bug update-manager

```
as above message says I got error
```

The problem cannot be reported:
This is not a genuine Ubuntu package

```


Following are the files in /etc/apts/sources.list
[http://paste.ubuntu.com/511416/](http://paste.ubuntu.com/511416/)
Then there are some files in /etc/apt/sources.list.d
their contents are
lucid-partner.list ---->[http://paste.ubuntu.com/511417/](http://paste.ubuntu.com/511417/)
 medibuntu.list---->[URL="http://paste.ubuntu.com/511418/ubuntu-mozilla-daily-ppa-lucid.list----"]http://paste.ubuntu.com/511418/
ubuntu-mozilla-daily-ppa-lucid.list----[/URL]>[URL="http://paste.ubuntu.com/511419/ubuntu-wine-ppa-lucid.list------------"]http://paste.ubuntu.com/511419/
ubuntu-wine-ppa-lucid.list------------[/URL]>[URL="http://paste.ubuntu.com/511420/lucid-partner.list.distUpgrade-----------"]http://paste.ubuntu.com/511420/
lucid-partner.list.distUpgrade-----------[/URL]>[http://paste.ubuntu.com/511421/](http://paste.ubuntu.com/511421/)
 medibuntu.list.distUpgrade---- ------->[http://paste.ubuntu.com/511422/](http://paste.ubuntu.com/511422/)

ubuntu-mozilla-daily-ppa-lucid.list.distUpgrade---->[URL="http://paste.ubuntu.com/511426/ubuntu-wine-ppa-lucid.list.distUpgrade---"]http://paste.ubuntu.com/511426/
ubuntu-wine-ppa-lucid.list.distUpgrade---[/URL]>[URL="http://paste.ubuntu.com/511427/lucid-partner.list.save---"]http://paste.ubuntu.com/511427/
lucid-partner.list.save---[/URL]>[http://paste.ubuntu.com/511428/](http://paste.ubuntu.com/511428/)
medibuntu.list.save---->[URL="http://paste.ubuntu.com/511430/ubuntu-mozilla-daily-ppa-lucid.list.save----"]http://paste.ubuntu.com/511430/
ubuntu-mozilla-daily-ppa-lucid.list.save----[/URL]>[URL="http://paste.ubuntu.com/511431/ubuntu-wine-ppa-lucid.list.save-----"]http://paste.ubuntu.com/511431/
ubuntu-wine-ppa-lucid.list.save-----[/URL]>[http://paste.ubuntu.com/511433/](http://paste.ubuntu.com/511433/)
 
What should I be checking now?

---

### Post by balkce on 2010-10-13
I had the same problem and this thread gave me the answer:

[http://ubuntuforums.org/showthread.php?t=1591435](http://ubuntuforums.org/showthread.php?t=1591435)

---

