---
title: "Can't get 15.10 to upgrade to 16.04"
date: 2016-04-29
forum: Installation &amp; Upgrades
---

### Post by Richard_Brown on 2016-04-29
Hi

I have run sudo apt-get update and then upgrade and then dist-upgrade and I don't get any upgrade prompt. Could my sources list be out of date please? Is there a way to force the upgrade please?

Thanks

Rich

---

### Post by Richard_Brown on 2016-04-29
Fixed it but updating my sources list.

Thanks

---

### Post by grahammechanical on 2016-04-29
dist-upgrade does not upgrade to a newer version of Ubuntu. It upgrades the existing installation by bringing packages that may have been held back for some reason.

The 16.04 release notes say this

> Set the "Notify me of a new Ubuntu version" dropdown menu to "For any new version" if you are using 15.10, Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. Software Updater should open up and tell you: New distribution release '16.04 LTS' is available. Click Upgrade and follow the on-screen instructions.

Users of Ubuntu 14.04 should note this comment

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

Regards

---

### Post by Richard_Brown on 2016-04-30
Thanks for the reply and thanks for the comment re dist-upgrade. I never realised that.

I have now started the update to 16.04.

Rich

---

