---
title: "Unable to upgrade due to problems in last upgrade"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by febros on 2014-04-22
Hi to all

I'm trying to upgrad from 13.10 to 14.10. I had to interrupt and resume the previous upgrade (from 13.04 to 13.10) and since then I have a couple of error messages when I boot, but I haven't had other problems until now.

When I run update-manager from terminal I get this message:

Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 108, in <module>
    print(_("Checking for a new Ubuntu release"))
UnicodeEncodeError: 'ascii' codec can't encode character '\xe0' in position 5: ordinal not in range(128)

---

### Post by TheFu on 2014-04-22
Welcome to the forums!
Ubuntu release numbers are named based on the month, so there wasn't an Oct 2014 release (14.10) .... we have to wait until ... October for that. ;)  However, 14.04 was released last week.  Ok, probably just a typo, no problem.

So, if do-release-upgrade isn't working, and the 13.10 install is 100%, fully updated and patched, then it is time to backup your data, settings and list of installed packages, perform a fresh installation of 14.04, then restore your settings, data, and list of packages into the freshly installed machine.  No ideal, but most things will work just fine without any more effort.

If you want to try to fix the 13.10 install problem, please post the relevant output from:
```
sudo aptitude update
sudo aptitude dist-upgrade

```
Use "code" tags please and do NOT post 50 lines of non-error output.  If that works cleanly (no warnings, no errors), then try 
```
sudo do-release-upgrade
``` and post the _relevant_ output from that command. **DO NOT RUN THIS UNTIL the update/dist-upgrade work flawlessly!**

---

### Post by febros on 2014-04-23
Thanks, it worked!

Yes, it was clearly a typo :) it was my first message in the forums because I've always solved other problems with previous posts, anyway I'm not a complete newbie on Linux.

So aptitude detected two packages that were mutually blocking their update (gnuplot-nox and gnuplot-x11). Once solved I was still not able to update via update-manager but do-release-upgrade worked fine.

---

### Post by TheFu on 2014-04-23
You will continue to have issues with updates until that package collision issue is resolved 100%.  Fix it now.

---

### Post by febros on 2014-04-28
Ok but... how can I try to fix it? Should I start a new thread?

---

### Post by TheFu on 2014-04-28
You should post the **relevant** output from the problem commands (update/upgrade) as requested above.

---

### Post by febros on 2014-05-02
not sure if this is the relevant code you were asking for

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-ca%40valencia
```

---

