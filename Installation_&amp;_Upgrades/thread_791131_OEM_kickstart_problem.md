---
title: "OEM kickstart problem"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by Centaur5 on 2008-05-11
I setup a network PXE install and put a custom kickstart file on the web server for it to get it's configurations but after completing the install and running oem-prepare-config it doesn't reset the oem user password after rebooting and creating a new user.  The new user inherits the password from the oem user so they must manually change their user password after logging in.  I'm attaching the kickstart config file so you can let me know if I did an incorrect configuration that is causing the issue.  Here is a bug filed on this problem but they say it's invalid:
[https://bugs.launchpad.net/bugs/47164](https://bugs.launchpad.net/bugs/47164)

---

### Post by Centaur5 on 2008-11-03
I found out the problem is that you can't have the password encrypted even though it's an option in Kickstart when generating the configuration file.  Now that I use a plain text password everything is fine.

---

