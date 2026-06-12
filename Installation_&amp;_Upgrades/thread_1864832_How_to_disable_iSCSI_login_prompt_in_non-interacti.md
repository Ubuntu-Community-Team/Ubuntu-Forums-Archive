---
title: "How to disable iSCSI login prompt in non-interactive kickstart"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by pwsouth on 2011-10-19
I'm trying to adapt our existing 11.04 kickstart/kickseed process to work with 11.10.  The new version prompts to log into iSCSI targets, although I don't think I did anything to enable that.  I don't use iSCSI and want to completely disable it during the install process.  I tried adding "iscsi=false" and "iscsi no" to the config file with no effect.

Just FYI in case it matters, our boot server is a CentOS box so some of the tools used to manage Ubuntu network boot resources don't exist on it.

Also I was unable to locate a manual which documents all of the options in the Ubuntu kickstart config file.

---

