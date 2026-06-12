---
title: "'apt (&gt;= 1.0.10.2ubuntu2)' is not installed -- cannot upgrade to 16.04"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2016-05-08
One of my two nearly identical desktop PCs will not start the upgrade to 16.04.  I get the error message "'apt (>= 1.0.10.2ubuntu2)' is not installed -- cannot upgrade to 16.04".  Only difference with PC that upgraded successfully is Windows partition is Win 10 64 Pro instead of Win XP Pro SP3.  Synaptic shows 1.0.10.2ubuntu1 is installed, and it is the latest version.  Package force version is greyed out.  PC is hard wired to Ethernet connection.

What do I need to do to fix problem?

Thank you,

John

---

### Post by ian-weisser on 2016-05-08
1.0.10.2ubuntu1 is the version in wily, not wily-updates (nor wily-security).
Your problem system seems to be not updating.
Update to the latest wily-updates and wily-security, then try release-upgrading.

---

### Post by cigtoxdoc on 2016-05-08
Thank you.

I did a sudo apt-get update && sudo apt-get upgrade a few more times and the program updated.  The wily-updates and wily security were appropriately ticked.  I suspect that the next time Ubuntu sends me the link to the upgrade, it will work.

John

---

