---
title: "gnome-shell freezing since upgraded to 18.10"
date: 2018-12-31
forum: Installation &amp; Upgrades
---

### Post by buisteric on 2018-12-31
Hi,
After I upgraded from 18.04 to 18.10, the system often doesn't boot, freezing with a black screen. I M able to SSH into it from another machine, did it, and ran Top to figure out that gnome-shell was taking 100% CPU and not responding. I'm not using GNOME, I'm running MATE, so I should not have a gnome-shell process at all. It seems to be GDM that runs gnome-shell. If I try systemctl restart gdm, nothing happens. If I try systemctl stop gdm, nothing happens either. Attempting to get logs just fails: dmesg, syslog and X.log have nothing of interest. Trying systemctl log gdm gives an error; it's probably yet another command and I cannot find it. Trying to kill GDM doesn't work either, only kill -9. There's more and more programs that do NOT respond to the kill signal, including e.g., Kodi, so I'm wondering why kill just doesn't wait 5 seconds and then falls back on a kill -9.
At this point, my Ubuntu system is pretty much unusable, requiring multiple attempts to start. There is no downgrade path to 18.04 other than clean install and it is time consuming to rebuild all my settings. I already tried in the past to separate the /home in a partition, but the /home always gets full on a SSD and cannot be enlarged without a time-consuming reorganization of the disk. I would need either downgrade paths, either a form of dynamic partitions that could be reorganized on the fly, but I guess this is pretty much impossible to achieve.
Anybody else having the same issue with gnome-shell? Any clue about how I could get logs about GDM?

---

### Post by curts on 2019-03-30
I haven't upgraded to 18.10, but I am going to make a suggestion based on the gnome-shell & gdm knowledge I have. On the RHEL platform, the recommended practice is to replace gdm with lightdm when using MATE as the primary window manager.

Hope this helps,

Curt

---

