---
title: "Questions about staging update(s)"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by bobmct on 2011-02-23
I am managing several Ubuntu servers that require release updates and eventually version updates.

I have a production server running 8.04 which needs updating asap.  But being production I'd like to be able to identify and download the updated modules prior to actually applying them so when the machine comes offline I can apply the updates without having to wait for the downloads.  Is this possible in CLI mode with this version using either apt-get or aptitude?  I also have several 9.04 systems with the same situation.

Any suggestions for those who may have been through this before greatly appreciated.  Thanks  :confused:

---

### Post by sryth on 2011-02-23
When you run update it should download every package necessary before attempting to apply any of them within versions, if you're updating to newer versions then that's different, you may have to download separately and apply in stages.

---

