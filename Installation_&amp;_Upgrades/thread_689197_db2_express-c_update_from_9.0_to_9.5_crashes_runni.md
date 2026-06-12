---
title: "db2 express-c update from 9.0 to 9.5 crashes running installation"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Norbert Munkel on 2008-02-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/db2exc-amd64/+bug/189538](https://bugs.launchpad.net/ubuntu/+source/db2exc-amd64/+bug/189538) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				If you are already running DB2 Express-C 9.0 (installed via ubuntu-packages) you will encounter problems with your running Databases as 9.5 is a real point release and not just a fixpack to 9.0. This needs special treatment of the running instance.

I have filed a bug (#189538) about this wrong behaviour including a first workaround. I would recommend to exclude the update from your list if you are already running 9.0 and have productive running databases.

---

