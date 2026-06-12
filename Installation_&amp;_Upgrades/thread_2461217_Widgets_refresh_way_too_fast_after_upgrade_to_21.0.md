---
title: "Widgets refresh way too fast after upgrade to 21.04 (and other issues)"
date: 2021-04-26
forum: Installation &amp; Upgrades
---

### Post by jmenax on 2021-04-26
Hi there,

I have recently updated from Ubuntu KDE Groovy (20.10) to Hirsute (21.04) and everything went Ok, no errors, just about 2 warnings (keep old configurations or not). Everything, seemingly, was working with no problems, but I found 2 things:

1. An error with CUPS service and Apparmor. The latter wont let even start the service and it keeps trying to start to infinity. A systemd-analyze showed that it never really starts from boot. TEMPORARY SOLUTION: disable apparmor for cups.

2. Some widgets use to show data in a nice way (maybe refreshing the data every 2 seconds). Now they put data almost 3 times per second. It becomes really annoying. The widgets are:

-Total CPU Use
-Hard disk activity

Haven't found a way to slow them down. 

Another thing is that before the upgrade total CPU usage while idle (clean boot and no applications open) was always about 1% to 3% (mostly below 2%), and now it fluctuates between 1% to 6% (mostly above 2%). I think kwin is the culprit here, but is not that big of a deal. Maybe it will be fixed soon, I hope.

Can I control the way those widgets behave via config files?

Regards,

---

