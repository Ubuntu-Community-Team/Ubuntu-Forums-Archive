---
title: "why wont my ubuntu 10.04 upgrade to 10.10"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Vokam on 2011-02-06
I am trying to upgrade my Ubuntu to 10.10. i've ran all the updates and when i get to press upgrade to 10.10 in the update manager, It gets a few files then first this message;

[COLOR="Blue"]Third party sources disabled
Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.[/COLOR]

On closing the window, it seems to continue installing, then this:

[[COLOR="blue"]COLOR="blue"]Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 [COLOR="blue"]This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
[/COLOR]
If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
[/COLOR]

Please help me out someone.
Thanks in advance.

---

### Post by kansasnoob on 2011-02-06
Look at what I've suggested here:

[http://ubuntuforums.org/showthread.php?t=1682856](http://ubuntuforums.org/showthread.php?t=1682856)

It's doubtful that you'll have the identical repo installed but maybe you'll understand the idea.

---

### Post by Vokam on 2011-02-24
> **kansasnoob said:**
> Look at what I've suggested here:

[http://ubuntuforums.org/showthread.php?t=1682856](http://ubuntuforums.org/showthread.php?t=1682856)

It's doubtful that you'll have the identical repo installed but maybe you'll understand the idea.
Thanks mate, I tried your suggestion, seems to have worked. Installed and even rebooted properly, but now the ubuntu 10.10 it won't start since the last time I shut it down. Am at my wits end. Any suggestions would be appreciated.Thanks

---

