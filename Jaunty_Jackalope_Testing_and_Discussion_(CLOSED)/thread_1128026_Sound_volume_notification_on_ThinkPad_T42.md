---
title: "Sound volume notification on ThinkPad T42"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by brunogirin on 2009-04-17
The sound volume feedback that appears in the notification area seems to have disappeared on my ThinkPad T42: when I change the volume using functions keys, the volume changes but the notification does not appear. It used to work as expected about 2 weeks ago and is no longer working. Interestingly, this problem seems limited to my ThinkPad: it works fine on my EeePC and both machines had latest updates applied last night.

Any pointers as to how to investigate this issue would be very much appreciated.

---

### Post by razaza on 2009-04-17
Same problem on my T60. Changing the volume works but no notification - not even the old one. Adjusting brightness does bring up the notification box.

---

### Post by toomin86 on 2009-04-17
> **brunogirin said:**
> The sound volume feedback that appears in the notification area seems to have disappeared on my ThinkPad T42: when I change the volume using functions keys, the volume changes but the notification does not appear. It used to work as expected about 2 weeks ago and is no longer working. Interestingly, this problem seems limited to my ThinkPad: it works fine on my EeePC and both machines had latest updates applied last night.

Any pointers as to how to investigate this issue would be very much appreciated.

The issue was caused by a recently pushed update to the hotkey-setup package in Jaunty.  Details can be viewed at the following link:

[https://lists.ubuntu.com/archives/jaunty-changes/2009-April/008919.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-April/008919.html)

After a far-too-long period of the same issue (volume buttons mapped to adjust both hardware and software volumes), it would seem they've decided to just scrap any and all software mappings for the Thinkpad hotkeys (I have a T60 as well, so I know the issue at hand). The end result is as you saw; anything software controlled will no longer function (like the suspend key), but anything hardware controlled (volume, brightness, thinklight, etc) will still function as normal, just without an OSD.

We're just gonna have to sit tight till someone comes up with a fix; at least the package managers are now aware of the issues we've been having.

-Toomin

---

### Post by brunogirin on 2009-04-17
> **toomin86 said:**
> The issue was caused by a recently pushed update to the hotkey-setup package in Jaunty.  Details can be viewed at the following link:

[https://lists.ubuntu.com/archives/jaunty-changes/2009-April/008919.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-April/008919.html)

Thanks for the info. Do you know if there is a bug filed in Launchpad for this issue?

---

### Post by toomin86 on 2009-04-17
> **brunogirin said:**
> Thanks for the info. Do you know if there is a bug filed in Launchpad for this issue?

The change was applied due to a previously filed bug; it looks like they're continuing discussion in the same thread:

[https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/355300](https://bugs.launchpad.net/ubuntu/+source/hotkey-setup/+bug/355300)

---

