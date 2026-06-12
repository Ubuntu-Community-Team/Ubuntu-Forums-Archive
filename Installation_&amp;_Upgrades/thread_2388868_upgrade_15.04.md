---
title: "upgrade 15.04"
date: 2018-04-08
forum: Installation &amp; Upgrades
---

### Post by corro692 on 2018-04-08
I am attempting to upgrade 15.04 to any LTS possible. 
The 15.04 repo throughs out 404 errors and "upgrade not available" so in order to update software I have reverted back to the 14.04 repo
When checking "ubuntu-support-status" I recieved

Traceback (most recent call last):
  File "/usr/bin/ubuntu-support-status", line 135, in <module>
    pkg.name, support_tag)
  File "/usr/bin/ubuntu-support-status", line 51, in get_maintenance_status
    raise Exception("No date tag found")

sudo do-release-upgrade gives 
 An upgrade from 'vivid' to 'xenial' is not supported with this tool.

---

### Post by QIII on 2018-04-08
Hello!

Support for 15.04 ended more than two years ago.  Its repositories have been moved to old-releases.

While you could update through each release in old-releases [this way]("https://help.ubuntu.com/community/EOLUpgrades"), it is extremely unlikely that success will result.  You are more likely to encounter a significant emotional event.

You best option is to back up all of your important files and do a clean installation of a [currently supported release]("https://wiki.ubuntu.com/Releases").  Although 14.04, 14.04.1 and 14.04.5 are currently supported, support will end in April of 2019, so they may not be worth your while.

---

### Post by corro692 on 2018-04-08
awesome! thank you for the reply

---

