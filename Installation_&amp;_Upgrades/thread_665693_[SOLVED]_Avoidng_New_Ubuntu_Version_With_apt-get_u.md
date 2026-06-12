---
title: "[SOLVED] Avoidng New Ubuntu Version With apt-get update/apt-get_upgrade"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2008-01-12
I like the ability to run apt-get-update followed by apt-get-upgrade on remote systems. 

When the next version of Ubuntu comes along, will apt-get-update/apt-get-upgrade automatically start the installation of the new available version, or will I be prompted not to do that?

---

### Post by kostkon on 2008-01-12
> **cmnorton said:**
> I like the ability to run apt-get-update followed by apt-get-upgrade on remote systems. 

When the next version of Ubuntu comes along, will apt-get-update/apt-get-upgrade automatically start the installation of the new available version, or will I be prompted not to do that?

No, don't worry. You have to explicity give *sudo apt-get dist-upgrade* to upgrade a system to a new version. As long as you do *sudo apt-get update && sudo apt-get upgrade* you will only get updates.

---

