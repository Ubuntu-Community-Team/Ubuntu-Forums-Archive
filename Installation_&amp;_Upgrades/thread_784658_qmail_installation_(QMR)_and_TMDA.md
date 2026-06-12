---
title: "qmail installation (QMR) and TMDA"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-05-06
I try to install qmail according qmailrocks. 
Qmail works, but many of the modules dont.

E.g. I could not use clamv, spamassassin, ...
Could anybody install it?

I got also a problem to install TMDA. With the spam amount it is really important to get it to work soon.
To add the line:

> | preline tmda-filter -S ~vpopmail/bin/vpopmail-vdir.sh

in .qmail-default resulted in:

> 
Traceback (most recent call last):
  File "/usr/bin/tmda-filter", line 53, in <module>
    execfile(os.path.join(execdir, 'tmda-rfilter'))
  File "/usr/bin/tmda-rfilter", line 37, in <module>
    from TMDA import Version
ImportError: No module named TMDA
Traceback (most recent call last):
  File "/usr/bin/tmda-filter", line 67, in <module>
    from TMDA.Defaults import LOGFILE_DEBUG
ImportError: No module named TMDA.Defaults


Any hints?

R.

---

### Post by ELMIT on 2008-05-16
Any hints? Has anybody installed TMDA / Qmail?

R.

---

