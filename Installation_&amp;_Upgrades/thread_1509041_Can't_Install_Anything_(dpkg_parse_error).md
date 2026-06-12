---
title: "Can't Install Anything (dpkg parse error)"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by vfiz on 2010-06-13
I just did a clean install of lucid today.  I went about installing all my normal programs, but now I can't install anything else.  When I try, I get this error: 
```
dpkg: parse error, in file '/var/lib/dpkg/status' near line 38072 package 'libxml-libxml-common-perl':
 error in Version string `1048576:': nothing after colon in version number
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

And my /var/lib/dpkg/status looks like this around that line:
```
Package: libxml-libxml-common-perl
Status: unknown ok not-installed
Version: 1048576:
```

Should I just delete this section from /var/lib/dpkg/status?

Just to be clear, this stops anything from installing now (also, autoremoving doesn't work), not just programs that mention libxml-libxml-common-perl.

---

### Post by limestone on 2010-06-13
try dpkg --configure -a in terminal

---

### Post by vfiz on 2010-06-13
Just tried it and got the exact same error.

---

### Post by vfiz on 2010-06-13
My impatience got the best of me.  I deleted the entry for libxml-libxml-common-perl from /var/lib/dpkg/status, and everything seems to be back to normal.  New programs install fine now.  I don't know if that's the best solution here, though.

---

