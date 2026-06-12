---
title: "dpkg fails with error"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by cfgauss on 2012-01-09
Whenever I *apt-get upgrade* I get this error at the end:

```
Removing latex-cjk-chinese ...
Running 'mktexlsr /usr/share/texmf /var/lib/texmf'.
This may take some time... done.
Building format(s) --byhyphen language.dat. This may take some time...
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.yseCywCh
Please include this file if you report a bug.

dpkg: error processing latex-cjk-chinese (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 latex-cjk-chinese
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I've tried to remove *latex-cjk-chinese* but it fails with this same error.

Any pointers would be gratefully received.

[SOLVED] update-manager indicated that my upgrade from 9.04 to 9.10 (first step towards 10.04) was partial. After it completed that upgrade, the problem went away. [/SOLVED]

---

### Post by squaregoldfish on 2012-01-09
```
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.yseCywCh

```

The log tells you where it's put the output of the failed process. What's in that file?

Steve.

---

