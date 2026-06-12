---
title: "No rebooting required in linux"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by poojasaraff on 2011-02-06
Why rebooting is not required in linux after installing an application even if related important files are running?

---

### Post by johncc on 2011-02-06
> **poojasaraff said:**
> Why rebooting is not required in linux after installing an application even if related important files are running?

Sometimes rebooting is required, sometimes not.  As the installation completes it will let you know whether you need to restart the computer "to complete the upgrade".  Why ask why?  :)

---

### Post by Rubi1200 on 2011-02-06
In general, the only time Linux needs to be rebooted is when there is an update/upgrade for the kernel.

However, as johncc pointed out, the system will let you know if and when this is needed.

---

### Post by ajgreeny on 2011-02-06
Another reason behind this is that in a linux OS the X GUI session runs on top of the kernel and basic OS.  The files updated and actually running at the time will continue to run until the next xsession starts.

When a new kernel comes along, you will be told that a reboot is needed, but having told you, the system will not decide to reboot all on its own, as another well known OS had a habit of doing, nor keeping on nagging you to do so.

---

