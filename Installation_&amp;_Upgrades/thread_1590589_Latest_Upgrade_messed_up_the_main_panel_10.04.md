---
title: "Latest Upgrade messed up the main panel 10.04"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by swaprava on 2010-10-08
Hi all,

I have upgraded all the possible upgrades in lucid on Oct 7, 2010. And since then the network applet and other applets moved to the right of the poweroff button in the main panel on the top of desktop. The upgrade log was as follows:

```

Aptitude 0.4.11.11: log report
Fri, Oct  8 2010 01:23:11 +0530

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 18 packages, and remove 0 packages.
77.8kB of disk space will be used
===============================================================================
[UPGRADE] coreutils 7.4-2ubuntu2 -> 7.4-2ubuntu3
[UPGRADE] dmsetup 2:1.02.39-1ubuntu4 -> 2:1.02.39-1ubuntu4.1
[UPGRADE] gdm 2.30.2.is.2.30.0-0ubuntu3 -> 2.30.2.is.2.30.0-0ubuntu4
[UPGRADE] libcouchdb-glib-1.0-2 0.6.3-0ubuntu1 -> 0.6.3-0ubuntu2
[UPGRADE] libdesktopcouch-glib-1.0-2 0.6.3-0ubuntu1 -> 0.6.3-0ubuntu2
[UPGRADE] libdevmapper1.02.1 2:1.02.39-1ubuntu4 -> 2:1.02.39-1ubuntu4.1
[UPGRADE] libgksu2-0 2.0.13~pre1-1ubuntu4 -> 2.0.13~pre1-1ubuntu4.1
[UPGRADE] libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.2 -> 1.8.1+dfsg-2ubuntu0.3
[UPGRADE] libk5crypto3 1.8.1+dfsg-2ubuntu0.2 -> 1.8.1+dfsg-2ubuntu0.3
[UPGRADE] libkrb5-3 1.8.1+dfsg-2ubuntu0.2 -> 1.8.1+dfsg-2ubuntu0.3
[UPGRADE] libkrb5support0 1.8.1+dfsg-2ubuntu0.2 -> 1.8.1+dfsg-2ubuntu0.3
[UPGRADE] libssl0.9.8 0.9.8k-7ubuntu8.1 -> 0.9.8k-7ubuntu8.3
[UPGRADE] mplayer 2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1 -> 2:1.0~rc3+svn20090426-1ubuntu16.1
[UPGRADE] mplayer-gui 2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1 -> 2:1.0~rc3+svn20090426-1ubuntu16.1
[UPGRADE] openssl 0.9.8k-7ubuntu8.1 -> 0.9.8k-7ubuntu8.3
[UPGRADE] python-imaging 1.1.7-1 -> 1.1.7-1ubuntu0.1
[UPGRADE] python-imaging-tk 1.1.7-1 -> 1.1.7-1ubuntu0.1
[UPGRADE] tar 1.22-2 -> 1.22-2ubuntu1
===============================================================================

Log complete.

```

I guess some of the coreutils are broken. Did anybody else face the same issue?

---

### Post by andrewthomas on 2010-10-09
```
rm -r ~/.gconf/apps/panel
```
this will restore your panel to the default.

---

### Post by swaprava on 2010-10-18
> **andrewthomas said:**
> ```
rm -r ~/.gconf/apps/panel
```this will restore your panel to the default.

Excellent. This works. however, be careful while using rm anytime. I wasn't careful and just copy pasted the command to my terminal, and didn't notice there was a gap between ~/ and the .gconf !! All my data was erased :( , luckily I had data backed up.

---

