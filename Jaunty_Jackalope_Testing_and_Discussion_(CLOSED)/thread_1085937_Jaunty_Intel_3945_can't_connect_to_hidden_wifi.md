---
title: "Jaunty Intel 3945 can't connect to hidden wifi"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ktraub on 2009-03-03
All,
After an upgrade to Jaunty Alpha 5 (from Intrepid) on my Dell Inspiron 9400 with the Intel 3945 internal WiFi, I can no longer connect to my router which uses a hidden ESSID.

I've tried rebooting the router and powering it off and rebooting and powering off the laptop and still no joy.

I can see other, broadcast ESSID's, but not my router with the hidden ESSID.

XP can connect to the hidden ESSID just fine and I was able to connect fine with Intrepid before the Jaunty upgrade.

Any help would be appreciated.
-Kev

---

### Post by MacUntu on 2009-03-03
AFAIK that's a known bug.

Hiding your ESSID is pointless anyways.

Edit: Here it is - [https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915](https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915)

---

### Post by ktraub on 2009-03-04
Thanks MacUntu!
The link with the work-around did the trick.
( [https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915](https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915) )

BTW, the hidden ESSID is not for security, it just cuts down the number of casual leeches as most of them just latch on to a neighboring unsecured access point.

Thanks again!
-Kev

---

### Post by sumwonyuno on 2009-03-06
I can connect to networks again.  Editing /lib/udev/rules.d/85-regulatory.rules, and adding "crda" to the last line worked for me.

Thanks

---

