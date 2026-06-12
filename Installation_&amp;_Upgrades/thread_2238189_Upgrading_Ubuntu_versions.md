---
title: "Upgrading Ubuntu versions"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by quindraco on 2014-08-06
Hi, all.

I'm running Ubuntu 12.04, and I'm running into some problems trying to update it.  

1)  I suppose my first question is, is it possible to update directly to 13.04?  I'm only primarily interested in LTS versions, so I don't actually want 12.10, but [this page]("https://help.ubuntu.com/community/UpgradeNotes") only lists instructions for 12.04->12.10->13.04.  Do I have to go through the version I have no interest in?

2)  Supposing I do, the instructions [here]("https://help.ubuntu.com/community/QuantalUpgrades") do not work.  Output:

```
Checking for a new Ubuntu release
Err Upgrade tool signature                                                                                                                                                                                          
  404  Not Found [IP: 91.189.91.14 80]                                                                                                                                                                              
Err Upgrade tool                                                                                                                                                                                                    
  404  Not Found [IP: 91.189.91.14 80]                                                                                                                                                                              
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                           
WARNING:root:file 'quantal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem. 

```

Any idea what I'm doing wrong, and how I can go about doing it correctly?

---

### Post by ajgreeny on 2014-08-06
You can't update to 13.04 as that version has now lost support.  You should soon, if not already, be offered the upgrade to 14.04, if you have your update manager set to show distro version upgrades.

14.04 is the only version available now to upgrade to, but I have always clean installed using a separate /home partition; much safer and less likely to corrupt the OS as far as I can make out from others.

---

### Post by kansasnoob on 2014-08-06
You wouldn't want to do that because Quantal is EOL:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You should be able to upgrade directly from 12.04 to 14.04 (Precise -> Trusty) but for some unknown reason it's not appearing in the update manager yet, I have filed a bug report:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826)

IMHO the best thing to do is make sure [software sources are set to upgrade only to LTS releases]("https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-Updates.png") and be patient.

---

### Post by grahammechanical on 2014-08-06
If you have problems updating 12.04, then you may have problems upgrading 12.04 to 14.04. Doing an upgrade to a newer version is not the way to fix updating problems. Unless, of course, you do a fresh install of the newer version.

Tell us about the updating problems. By the way, before upgrading to a newer version it is best to disable any PPAs that we have used to install software and switch to using an open source video driver.

Regards.

---

### Post by Rob Sayer on 2014-08-07
> **ajgreeny said:**
> ... 14.04 is the only version available now to upgrade to, but I have always clean installed using a separate /home partition; much safer and less likely to corrupt the OS as far as I can make out from others.

Agree 100% with reinstalling rather than upgrading ... it's more reliable.

Also with a separate /home partition if you have enough partitions available.  It's not nearly as hard as it sounds at first, and you will retain your data and user settings for software when you reinstall.  Have your data backed up first of course ....

---

