---
title: "LTSP Blank Desktop Screen on Client"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by aarat on 2012-07-23
I have setup ltsp server as described. Everything works well. Clients are able to login without any issues. The only issue I am facing is after logging on to the login screen that I am not able to see the menu bar. I am able to change desktop background, create launcher and see the right click stuff when we click on the desktop.

I have tried below editions and was able to replicate the same.

1.) Ubuntu 12.04 alternate CD
2.) Ubuntu 10.04 alternate CD
3.) Ubuntu 10.04 Desktop with ltsp-standalone installation.

The desktop environment loads good on server and works normally. The issue is only occuring with the clients.

PS: I have multiple LAN cards installed on the system. Primary connects to the client network. Secondary connects to the internet.

---

### Post by aarat on 2012-07-24
Got it fixed by adding below lines to lts.conf

[MAC Address of Client]
XRANDR_OUTPUT_0="VGA1 --off"

---

