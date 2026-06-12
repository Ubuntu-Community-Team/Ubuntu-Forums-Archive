---
title: "Login screen appears on second monitor"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by Olivares on 2020-06-15
I upgraded from Ubuntu 18.04 to 20.04 yesterday. Now the login screen pops up on my second monitor (smart TV linked by HDMI cable). Once logged in, desktop correctly appears on first monitor. I have researched remedies. I copied .conf/monitor.xml to  /var/lib/gdm3/ but this didn't solve my problem. Another suggestion was to change /etc/gdm3/custom.conf and uncomment the line #WaylandEnable=false. This had the effect of making the GRUB menu appear on the second monitor and the login screen and desktop appear on the first monitor. So I undid my change to this file. As a short term solution i can unplug the second monitor, but suggestions for a permanent solution would be appreciated. ):P

---

