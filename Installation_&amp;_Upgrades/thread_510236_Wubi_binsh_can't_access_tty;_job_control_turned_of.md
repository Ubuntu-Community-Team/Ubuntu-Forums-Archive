---
title: "Wubi: /bin/sh: can't access tty; job control turned off"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Eminem on 2007-07-26
I've had Ubuntu installed through Wubi for a while now (few days), and everything worked fine.

Last night, it was working just fine; but when I booted into Ubuntu this morning--the Ubuntu boot screen wouldn't go past 10% and then it would go to a screen that read "/bin/sh: can't access tty; job control turned off".

Any help?

---

### Post by Sef on 2007-07-28
Check out[ this post]("http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off").

---

### Post by n3hu on 2008-01-11
I had the same problem tonight with my Wubi install.
To fix it I ran "chkdsk /f" from windows xp. I actually
booted using "ultimate boot cd for windows" which may
or may not have been necessary. For a more detailed
check (it takes forever) you can run "chkdsk /r".

  If that didn't work, plan-B was to restore the wubi
directory (in windows) from my backup/recovery
copy on a usb drive.

gl

---

