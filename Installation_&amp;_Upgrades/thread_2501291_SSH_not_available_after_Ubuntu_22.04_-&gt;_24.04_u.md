---
title: "SSH not available after Ubuntu 22.04 -&gt; 24.04 upgrade"
date: 2024-09-30
forum: Installation &amp; Upgrades
---

### Post by captbunzo on 2024-09-30
Hi all,

I recently upgraded a small dedicated server of mine from Ubuntu 22.04 to 24.04. I followed the instructions on this page:

[INDENT][https://ubuntu.com/server/docs/how-to-upgrade-your-release](https://ubuntu.com/server/docs/how-to-upgrade-your-release)[/INDENT]

The system successfully booted up after apt update/upgrade. And by successfully booted up I mean came up, I could login with SSH, and everything looked good. However, after do-release-upgrade, not so much. The system will not come up to the point that I can login via SSH.

However, I can boot it up in rescue mode and mount the filesystems. However, I am at a loss as to what logs to examine to figure out what is going on.

Any advice?

Thanks,
Paul Thompson

---

### Post by ian-weisser on 2024-09-30
> **captbunzo said:**
> The system will not come up to the point that I can login via SSH.

Systemd has multiple boot targets. Please be specific. Which target does the server boot to successfully, and which unsuccessfully? 

Review your logs. What errors are recorded? If possible, please try to show us exact, complete error messages.

---

### Post by captbunzo on 2024-10-01
The server is with OneProvider and I am not sure how to configure the system to boot to a specific boot target.

When I say that it will boot into rescue mode, I mean that there is an "Ubuntu-18.04_amd64" image that I can select in a menu on the control panel for the server and hit boot into rescue mode. After a few minutes I can connect via SSH to a system with a username and password provided on that screen.

Then I can mount /dev/sda1 (which has System.map, initrd, and vmlinuz files in it) and /dev/sda2 (which is / of the system).

---

