---
title: "Ubuntu 11.10 post installation update hangs"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by asarkar on 2011-10-29
After successfully running Ubuntu 11.10 64-bit for about 2 weeks, I attempted an update using the update-manager. It's been an hour now and the update is stuck at the same position. Attached is a screenshot. Of course, there is no option to cancel it and I may end up hard reboooting the system.

---

### Post by raja.genupula on 2011-10-29
have you tried doing update from terminal ? 

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by asarkar on 2011-10-29
Same result, update freezes after getting the changelog. Following is what I am looking at for 30 minutes now.

...

Get:1 Changelog for xserver-common ([http://changelogs.ubuntu.com/changelogs/pool/main/x/xorg-server/xorg-server_1.10.4-1ubuntu4.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/x/xorg-server/xorg-server_1.10.4-1ubuntu4.2/changelog)) [272 kB]
xorg-server (2:1.10.4-1ubuntu4.2) oneiric-proposed; urgency=low

  * Fix crash on accepting a touch grab from an indirect device (LP: #877825)
    - Added 510_fix_touchpad_touch_event_removal.patch

 -- Chase Douglas <chase.douglas@ubuntu.com>  Tue, 18 Oct 2011 17:33:31 -0700

(END)

---

