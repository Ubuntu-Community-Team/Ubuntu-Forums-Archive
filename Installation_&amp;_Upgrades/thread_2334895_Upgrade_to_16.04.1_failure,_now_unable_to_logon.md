---
title: "Upgrade to 16.04.1 failure, now unable to logon"
date: 2016-08-23
forum: Installation &amp; Upgrades
---

### Post by Trakwup on 2016-08-23
Hello,

First, please understand that I am both new to Ubuntu and to the forums. If there are log and/or other details that should be commonly included in such a post, please let me know.

After recently accepting the upgrade to v16.04.1, the upgrade process did report some error messages, but unfortunately I did not record them. At some point towards the end of the upgrade, I was presented the "System program problem detected / Do you want to report the problem now?" dialog box. I rebooted the machine, and now this same error pop-up is displayed immediately post-logon, and the entire system becomes entirely unresponsive. The desktop/Unity is never displayed. The error message remains on the screen, and while the mouse moves around, I am unable to click on "Cancel" or "Report problem". Prior to logon, there is no indication of any problem; I am able to initiate a shutdown, disconnect the network, etc.

FYI, the machine is a VM sitting in an ESXi server. Neither telnetd nor SSH has ever been enabled since I've always just used the vSphere client to connect.

Any ideas on how I can recover?

Thanks!

EDIT: Note that I did of course come across the many other posts herein relating to the error message quoted, however none of those articles appeared applicable when I'm unable to logon.

---

### Post by fenrice on 2016-10-24
Try "control-alt-f6" and see if you can get a prompt and investigate from there. Use top to look for 99% cpu usage, dmesg to look for strange messages (possible errors you can google for), in /var/log messages to see if anything looks out of sorts. Upgrades usually go smooth, but every system is different and sometimes they don't, this is why they always warn you to backup data. You can also try to say install xubuntu or some other desktop and see if you can get in that way (just select the alternative session in the login menu. I hope this help a little.

---

### Post by Trakwup on 2016-10-24
> **fenrice said:**
> Try "control-alt-f6" and see if you can get a prompt and investigate from there. Use top to look for 99% cpu usage, dmesg to look for strange messages (possible errors you can google for), in /var/log messages to see if anything looks out of sorts. Upgrades usually go smooth, but every system is different and sometimes they don't, this is why they always warn you to backup data. You can also try to say install xubuntu or some other desktop and see if you can get in that way (just select the alternative session in the login menu. I hope this help a little.

Thanks very much for the tip. Alas, after a while I gave up and ended up rebuilding the machine from scratch.

---

