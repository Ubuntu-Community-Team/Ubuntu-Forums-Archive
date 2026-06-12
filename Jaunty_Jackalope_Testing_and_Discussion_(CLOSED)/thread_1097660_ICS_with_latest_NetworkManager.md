---
title: "ICS with latest NetworkManager"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Eestlane on 2009-03-16
There is an option to choose shared IP for a connection in latest NetworkManager in Jaunty Alpha 6, but it seems it does not work.

Should it function, or is just a placeholder in GUI?

If it does not work yet, I probably need to go through messing with it [manually]("https://help.ubuntu.com/community/Internet/ConnectionSharing").

Thank you in advance.

---

### Post by Eestlane on 2009-03-26
Could anyone confirm that it's meant to be not working yet?

---

### Post by uBeer on 2009-03-26
Well, to get is working: install dnsmasq-base or something like that. After that it'll work.

Maybe there should be a bug report that dnsmasq-base should be included in the default install, or only show the option when dnsmasq-base has been installed.

---

### Post by Eestlane on 2009-03-26
Thankyou, I'll try that as soon as I have time.

EDIT: Seems the bug report exists already:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/340857](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/340857)

Going to test it out now...

EDIT2: It works now indeed. Super :) Thankyou for the hint again.

---

