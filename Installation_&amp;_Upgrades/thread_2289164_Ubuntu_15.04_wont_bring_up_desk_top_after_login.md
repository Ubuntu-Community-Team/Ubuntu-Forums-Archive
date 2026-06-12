---
title: "Ubuntu 15.04 wont bring up desk top after login"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by porchkracker on 2015-08-01
Just installed ubuntu 15.04 on a dell dimension e520, install went great took all updates. When it wanted to be  restarted, it let me login,  and only brings up the ubuntu screen with the ubuntu logo in lower left corner. No launcher or anything.

---

### Post by ubfan1 on 2015-08-02
Does the "guest session" have a desktop?  Sometimes the "dot"files (hidden, first character is a . ) cause some problems in a user's home directory.  If the guest works, try just deleting all the "dot" files and directories (starting with .Xauthority ).

---

