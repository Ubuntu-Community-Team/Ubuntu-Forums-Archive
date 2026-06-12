---
title: "Upgrade to maverick fails on 'nut' package"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by hymerman on 2010-11-28
Hi, I've just upgraded to maverick and all has gone well bar one package, nut (Network UPS Tools).

The end of the "sudo do-release-upgrade" command, and the output of any subsequent "sudo apt-get upgrade" commands, shows this:

```
Setting up nut (2.4.3-1ubuntu5) ...
sed: -e expression #1, char 21: unterminated 's' command
dpkg: error processing nut (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nut
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas what the problem is, or how to fix it? I've searched the forum, google and the bug list for anything similar but can't find anything useful.

---

