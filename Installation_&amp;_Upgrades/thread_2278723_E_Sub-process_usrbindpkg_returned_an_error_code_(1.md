---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1) - OpenNMS Install"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by mike_m2 on 2015-05-18
Hello everyone!

So I'm trying to install OpenNMS on the latest Ubuntu. I've followed all of the prerequisite steps very carefully and I've come to the step where I finally install OpenNMS but the problem is I'm given the below error. I've seen other people who have been given the same error but with different processes and I'm unsure how to continue. I've tried to install different Java versions without any luck and I'm all out of ideas. I'm still learning the ins and outs of Linux so I apologize in advance if this is a simple fix and I just missed it. Does anyone have any ideas on what I can do?


[FONT=courier new]Setting up roaraudio (1.0~beta11-1) ...
Starting RoarAudio: invoke-rc.d: initscript roaraudio, action "start" failed.
dpkg: error processing package roaraudio (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up slpd (1.2.1-9) ...
+ [ configure = configure ]
+ dpkg --compare-versions  le 1.2.1-7.6
+ echo Reinstalling init script for new priorities ...
Reinstalling init script for new priorities ...
+ update-rc.d slpd remove
update-rc.d: /etc/init.d/slpd exists during rc.d purge (use -f to force)
dpkg: error processing package slpd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 roaraudio
 slpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

[/FONT]

---

### Post by Alexis_Lopez on 2015-05-23
There is a known bug with slpd that is causing this issue.  I'm having the same problem, not sure how to fix.

---

