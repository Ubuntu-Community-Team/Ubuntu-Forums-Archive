---
title: "Live CD won't install"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by Dipper on 2012-05-28
I used remastersys to create a live CD (Precise).  The installer will not open.  I tried running ubiquity in the konsole and this is the output:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 155, in <module>
    main()
  File "/usr/bin/ubiquity", line 53, in main
    with open('/proc/%d/oom_score_adj' % os.getpid(), 'w') as fp:
IOError: [Errno 2] No such file or directory: '/proc/2340/oom_score_adj'

What's the fix?

---

### Post by HalfNote5 on 2012-05-28
Out of curiosity, what version of Remastersys are you using?   I had an odd quirk a while back due to using a WAY outdated version.

---

