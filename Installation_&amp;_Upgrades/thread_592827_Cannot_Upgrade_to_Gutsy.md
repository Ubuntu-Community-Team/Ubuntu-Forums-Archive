---
title: "Cannot Upgrade to Gutsy"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by mike_302 on 2007-10-26
I get an error when trying to upgrade my 64Feisty to Gutsy from the Upgrade manager. It tells me to go make the error report and go to var/log/dist-upgrade , and I did, and opened the log, and this is what I found:

> 2007-10-26 16:17:38,845 INFO release-upgrader version '0.81' started
2007-10-26 16:17:39,216 DEBUG lsb-release: 'feisty'
2007-10-26 16:17:39,216 DEBUG _pythonSymlinkCheck run
2007-10-26 16:17:41,029 DEBUG checkViewDepends()
2007-10-26 16:17:41,030 DEBUG getRequiredBackports()
2007-10-26 16:17:41,032 ERROR IOError in cache.update(): 'Failed to lock /var/lib/apt/lists/lock'. Retrying (currentRetry: 0)
2007-10-26 16:17:41,033 ERROR IOError in cache.update(): 'Failed to lock /var/lib/apt/lists/lock'. Retrying (currentRetry: 1)
2007-10-26 16:17:41,033 ERROR IOError in cache.update(): 'Failed to lock /var/lib/apt/lists/lock'. Retrying (currentRetry: 2)
2007-10-26 16:17:41,033 ERROR doUpdate() failed complettely
2007-10-26 16:17:42,934 ERROR Can not find backport 'release-upgrader-apt'

So what do I do?
Another side question, is upgrading form the upgrade manager going to mean that the Gutsy will be 64-bit too?

---

### Post by mike_302 on 2007-10-26
btw, its a gateway mx6425 laptop. 1 GB RAM, amd turion 64, ATI Radeon XPRESS 200M .

---

