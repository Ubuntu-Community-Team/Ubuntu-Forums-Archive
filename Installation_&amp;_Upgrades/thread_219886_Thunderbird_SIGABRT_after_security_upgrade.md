---
title: "Thunderbird SIGABRT after security upgrade"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by steffen on 2006-07-20
After last Dapper security upgrade to Thunderbird 1.5.0.4 I'm not able to read Thunderbird email any more. I am able to start Thunderbird and play around with preferences, extensions, etc. but as soon as I try to check any of my IMAP folders Thunderbird crashes and dies. Opening local folders works. I have deleted all my extensions and the chrome directory, withouth improvement.

When starting Thunderbird from command line, I get the following:
```
steffen@silicom:/usr/bin $ ./mozilla-thunderbird
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 terminate called after throwing an instance of 'std::bad_alloc'
  what():  St9bad_alloc
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 17557 Avbrutt (SIGABRT)       "$prog" ${1+"$@"}
```

The script outputs "DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 -->" when Thunderbird starts. I can then browse around the software for as long as I want, until I check an IMAP folder. Then Thunderbird will start to look for messages, and as it says "opening folder" Thunderbird will crash with the "terminate" error.

Any help appreciated!

---

### Post by steffen on 2006-07-24
I have tried to install the Thunderbird directly from [www.mozilla.com](www.mozilla.com). I'm still not getting further, leading me to believe this is a shared library issue. The software still exits when downloading IMAP folders, with the same error.

---

### Post by steffen on 2006-07-25
After a lot of debugging and experimenting, I've found out that the issue was with the spam training filter. After deleting training.dat, everything is working allright, and I'm pretty sure training.dat was the issue - if anyone else encounters the same problem, try this first.

I've kept the same training.dat file across several computers for quite a few years though. It's sad to throw away such a well trained spam filter, but it's served me well since Thunderbird 0.1. At least it's usable again now.

---

