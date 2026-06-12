---
title: "EM64 install failure: dmraid"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by Nachtengel on 2006-06-24
Hello all, I am following the directions at [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

and am on the step where I am installing dmraid.

I type:

```
root@HOST:/# apt-get install dmraid
Reading package lists... Done
Building dependency tree... Done
dmraid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up dmraid (0.9.9+1.0.0.rc9-2ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
 * Setting up DMRAID devices... invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: error processing dmraid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Obviously I am having some issues with dpkg, but what am I to do?

---

