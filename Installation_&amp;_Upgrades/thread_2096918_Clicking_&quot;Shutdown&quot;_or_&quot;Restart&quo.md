---
title: "Clicking &quot;Shutdown&quot; or &quot;Restart&quot; link exits to &quot;Login&quot; screen"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by rrnbtter on 2012-12-21
Greetings,
I am reporting and solving this problem at the same time.
Problem: Usually after an update the Shutdown and Restart links resolve to the Login screen. 
Numerous work-arounds are available for this problem but they only work on the reported machines not in all cases.
This problem quite often happens when the Home folder is encrypted.
This problem spans from Lucid to the Development RR13.04. 
It occurred Dec 18, 2012 on my Raring 13.04 system. 

This solution involves creating a "local shutdown policy" instead of editing the shutdown policy in the root folder which could create problems later on.

INSTRUCTIONS
 1. In a terminal create an empty file "/etc/polkit-1/localauthority/50-local.d/usershutdown.pkla

code: in a terminal enter the following.
sudo gedit /etc/polkit-1/localauthority/50-local.d/usershutdown.pkla

2. Copy and Paste the following into the file and Save.

[Allow Shutdown]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=yes
ResultInactive=yes
ResultActive=yes

[Allow Restart]
Identity=unix-user:*
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=yes
ResultInactive=yes
ResultActive=yes

You are done you may need a reboot but your shutdown should now work correctly.

---

