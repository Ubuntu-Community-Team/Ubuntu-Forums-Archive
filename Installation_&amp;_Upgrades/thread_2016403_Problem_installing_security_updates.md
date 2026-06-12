---
title: "Problem installing security updates"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by slucile on 2012-07-04
Hello - I am experiencing a problem installing security updates.  I get an error message that reads:

Could not calculate the upgrade
        [LEFT]An unresolvable problem occurred while calculating the upgrade.[/LEFT]
        [LEFT]Please report this bug against the 'update-manager' package and include the following error message:[/LEFT]
    [LEFT]'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'


Can someone help me to figure out how I report this and how to fix the problem?  thanks.
[/LEFT]

---

### Post by fantab on 2012-07-04
Try from Terminal (Ctrl+Alt+T):

```
sudo apt-get update
sudo apt-get upgrade
```

To Report a BUG see [**HERE**]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by slucile on 2012-08-05
Thanks!  I did both of those commands and I think it mostly worked but there are few remaining error messages.  I&#699;m not sure if any are fatal flaws or not.  However, I notice when I start update manager from my menu bar I still get the error message I originally got.

Can you help me interpret the remaining errors - below?

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 357278 files and directories currently installed.)
Preparing to replace ttf-lyx 2.0.2-1~getdeb1 (using .../ttf-lyx_2.0.3-1~getdeb1_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 8: dpkg-maintscript-helper: not found
Unpacking replacement ttf-lyx ...
/var/lib/dpkg/info/ttf-lyx.postrm: 6: dpkg-maintscript-helper: not found
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 6: dpkg-maintscript-helper: not found
dpkg: error processing /var/cache/apt/archives/ttf-lyx_2.0.3-1~getdeb1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/info/ttf-lyx.preinst: 8: dpkg-maintscript-helper: not found
/var/lib/dpkg/tmp.ci/postrm: 6: dpkg-maintscript-helper: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Preparing to replace openoffice.org-emailmerge 1:3.2.0-7ubuntu4.2 (using .../openoffice.org-emailmerge_1%3a3.2.0-7ubuntu4.3_all.deb) ...
Disabling: mailmerge.py

unopkg done.
Unpacking replacement openoffice.org-emailmerge ...
Preparing to replace libc-bin 2.11.1-0ubuntu7.8 (using .../libc-bin_2.11.1-0ubuntu7.10_i386.deb) ...
Unpacking replacement libc-bin ...
Processing triggers for fontconfig ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/ttf-lyx_2.0.3-1~getdeb1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

