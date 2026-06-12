---
title: "Codeblocks installation problems"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by resistantgnome on 2007-07-20
I tried this on terminal **sudo dpkg -i CB_20070715_rev4266_Ubuntu6.10+7.04_wx2.8.4.deb **
Got few errors. Can anyone help me to move ahead
```

(Reading database ... 130089 files and directories currently installed.)
Preparing to replace codeblocks 1.0svn-rev4266 (using CB_20070715_rev4266_Ubuntu6.10+7.04_wx2.8.4.deb) ...
Unpacking replacement codeblocks ...
dpkg: dependency problems prevent configuration of codeblocks:
 codeblocks depends on libwxbase2.8-0 (>= 2.8.4.0); however:
  Version of libwxbase2.8-0 on system is 2.8.1.1-0ubuntu4.
 codeblocks depends on libwxgtk2.8-0 (>= 2.8.4.0); however:
  Version of libwxgtk2.8-0 on system is 2.8.1.1-0ubuntu4.
dpkg: error processing codeblocks (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 codeblocks

```

PS: I posted the same question on Absoluter beginner forum but people there say it's not beginner question so I posted here again.

---

### Post by JesterDev on 2007-07-20
I replied to your post in the beginners section, however I read your post wrong the first time and edited my post after you had already posted again. :)

Anyway...

It looks like you need to upgrade to the latest version(s) of ibwxbase and libwxgtk as the ones you have installed are older.

---

### Post by mandrav on 2007-07-20
Read [this document]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu") (the section about wx2.8.4).

---

### Post by resistantgnome on 2007-07-20
Thanks. I've installed the older SVN build. It's working fine.

---

