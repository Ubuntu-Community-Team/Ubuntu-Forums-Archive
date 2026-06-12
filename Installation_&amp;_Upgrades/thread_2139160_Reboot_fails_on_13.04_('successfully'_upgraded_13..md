---
title: "Reboot fails on 13.04 ('successfully' upgraded 13.04 from 12.10)"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by fragtion on 2013-04-26
Hi all,

Servers booted into 13.04 fine the first time after the upgrade, although I still saw the MOTD notice "New release '13.04' available.\nRun 'do-release-upgrade' to upgrade to it." after booting into 13.04

So I refreshed apt (update / dist-upgrade... 0 changes) and rebooted again...

This time, rather than completing the reboot...:
> * Asking all remaining processes to terminate...
* Killing all remaining processes... [fail]
* Will now switch to single-user mode
Give root password for maintenance
(or type Control-D to continue):
still pingable, but sshd dead... frustrating for dedicated servers

---

### Post by fragtion on 2013-04-26
Bump: Anyone else with this problem? I've experienced it on all machines (5 in total) that I've updated from 12.10 to 13.04.. two of those were dedicated headless servers and I've had to pay for onsite technician call-outs for hard-reset =/

---

### Post by fragtion on 2013-04-27
Update: I've found that this only seems to happen when I issue "reboot now" rather than "reboot". The thing is, I've always used 'reboot now' and it always used to always work the same way (afaik, some distro's require 'now' / do nothing without arguments). Now it seems to be a potential trap that causes the machine not to reboot... I can't for the life of me understand why "reboot now" should bring the box to console maintenance mode anyway...?

> root@server:~# reboot
Broadcast message from root@server
        (/dev/pts/0) at 00:00 ...
The system is going down for reboot NOW!
> root@server:~# reboot now
Broadcast message from root@server
        (/dev/pts/0) at 00:00 ...
The system is going down to maintenance mode  NOW!

I'm guessing this is a bug and should be filed as such?

---

### Post by labsin on 2013-04-29
> **fragtion said:**
> Update: I've found that this only seems to happen when I issue "reboot now" rather than "reboot". The thing is, I've always used 'reboot now' and it always used to always work the same way (afaik, some distro's require 'now' / do nothing without arguments). Now it seems to be a potential trap that causes the machine not to reboot... I can't for the life of me understand why "reboot now" should bring the box to console maintenance mode anyway...?




I'm guessing this is a bug and should be filed as such?

I'm having the same issue. Did you already file a bug?
Could you share a link to it.

---

### Post by fragtion on 2013-04-29
> **labsin said:**
> I'm having the same issue. Did you already file a bug?
Could you share a link to it.
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1174272](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1174272)

---

### Post by granthays on 2013-05-16
This happened to me with the command "sudo reboot -h now". From the bug tracker, it seems the preferred method for rebooting is without a time now? I haven't tried it yet. Any other word on this?

---

