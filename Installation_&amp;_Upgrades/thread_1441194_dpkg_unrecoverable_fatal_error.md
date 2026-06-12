---
title: "dpkg: unrecoverable fatal error"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by subman on 2010-03-28
> dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `sysvinit-utils': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


This is the error i get when i try to update my system, fresh install of ubuntu 9.10

:(

---

### Post by indiepop on 2010-04-11
i am experiencing a similar problem.  my error reads as follows:

```
dpkg: unrecoverable fatal error, aborting:
 conflicting diversions involving `/usr/lib/gnupg/gpgkeys_curl.non_curl' or `/gnupg-curl'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

nothing i've tried fixes it and i've googled for a solution for hours now.  help.

---

### Post by mac9416 on 2010-04-11
subman, I wouldn't venture a guess if it hadn't been a week since you posted, but I'll do what I can.

> failed in buffer_read(fd): files list for package `sysvinit-utils': Input/output error

That kinda sounds like a problem with a corrupt package. Perhaps you should try running 'sudo apt-get clean' to delete all cached package files, then try to install again.

indiepop, I've never seen anything quite like the error you're getting, so I'm afraid I can't offer any suggestion. Sorry.  :(

---

