---
title: "Error: insserv rejected the script header"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by panja on 2017-01-23
Good afternoon!

An Ubuntu n00b here. :cool:
I'm a Windows sys admin, my daily driver is a Macbook with OSX and running a few VPS servers with Ubuntu since a few months.
I'm pretty new to Ubuntu (Linux) but I've been running it on my VPS servers for months now without any problems until today.

When I do a "sudo apt-get update && sudo apt-get upgrade" I'm getting errors on 2 Ubuntu machines.
```

Setting up util-linux (2.27.1-6ubuntu3.2) ...
insserv: warning: script 'S06obmaua' missing LSB tags and overrides
insserv: warning: script 'S02obmscheduler' missing LSB tags and overrides
insserv: warning: script 'obmscheduler' missing LSB tags and overrides
insserv: warning: script 'obmaua' missing LSB tags and overrides
insserv: Starting obmaua depends on vmcontext and therefore on system facility `$all' which can not be true!
insserv: Starting obmaua depends on vmcontext and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service obmaua and vmcontext if started
insserv:  loop involving service vmcontext at depth 5
insserv:  loop involving service obmaua at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can someone help me out to install the latest updates?

Running:
Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-59-generic x86_64)

---

### Post by ian-weisser on 2017-01-23
You installed two services sometime in the past called 'obmaua' and 'obmscheduler'. The scripts should be in /etc/init.d/
1) The headers on both of those files are incomplete or broken - fix them. Other scripts in /etc/init.d have proper headers - use them for examples.
2) obmaua depends upon another script, 'vmcontext'..which unwisely depends upon 'all'.  'All' includes obmaua, creating a loop. init dependency loops are very bad. Fix it.
Now read the error messages again, in order. Do they make more sense now?

You will not receive Ubuntu security updates until you fix those two problems.

If you installed those scripts from a third-party vendor, consider changing vendors. Initscripts are *two* generations behind. For Ubuntu 16.04 and later, vendors should be providing services for systemd.

---

### Post by panja on 2017-01-23
Thanks ian for your reply!
Both script are indeed 3rd party scripts and belong to Ahsay OBM backup software.

I found this article on the Ahsay KB:
[https://forum.ahsay.com/viewtopic.php?f=117&t=10078](https://forum.ahsay.com/viewtopic.php?f=117&t=10078)

My problem has been resolved now

Many thanks ian, for pointing me to the right direction.

---

### Post by ian-weisser on 2017-01-23
Since it's not Ubuntu software, have you looked in the Ahsay forums? Couple threads there about the problem...

Initscripts in Debian and Ubuntu should include an [LSB-compliant]("https://wiki.debian.org/LSBInitScripts") header. The system expects those, and lack of a proper header will (as you see) generate warnings.
The headers describe the order to bring up/down serves upon startup or shutdown or runlevel change. Runlevels are a sysvinit concept, not used in Upstart or systemd.

---

### Post by panja on 2017-01-23
I think our posts crossed each other. :)
The problem is resolved for me. 

Again, thanks for pointing me towards the right solution.

---

