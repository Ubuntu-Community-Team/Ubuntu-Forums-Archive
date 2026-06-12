---
title: "Gnome boot-loop on Admin account after GPU Upgrade"
date: 2019-01-07
forum: Installation &amp; Upgrades
---

### Post by iandol on 2019-01-07
Hi, I'm using a standard Ubuntu 18.04 (GDM and Gnome under XOrg) and a Dell workstation. I was using an AMD Radeon Pro card but moved over to an NVidia GTX 2070. I managed to disable the Noveau drivers and install the Nvidia proprietary drivers, and it seems to work fine (Nvidia drivers are running). But my main admin account is not lot logging in, I get a boot loop when I enter my user password. Another account (non-admin), logs in just fine, so there is something in my settings. Looking at /var/log/syslog it seems that **MIT-MAGIC-COOKIE-1 **is causing the problem. I did have an _.ICEAuthority_ but deleted it based on advice on how to fix boot loop: it didn't work. I  don't have an _.XAuthority_ file.```

Jan  8 09:59:17 cog1 gnome-session[7218]: Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused
Jan  8 09:59:17 cog1 gnome-session-c[7482]: cannot open display: :0.0
Jan  8 09:59:17 cog1 gnome-session[7218]: Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused
Jan  8 09:59:17 cog1 gnome-session-c[7483]: cannot open display: :0.0
Jan  8 09:59:17 cog1 gnome-session[7218]: gnome-session-binary[7218]: WARNING: software acceleration check failed: Child process exited with code 1
Jan  8 09:59:17 cog1 gnome-session[7218]: gnome-session-binary[7218]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan  8 09:59:17 cog1 gnome-session-binary[7218]: WARNING: software acceleration check failed: Child process exited with code 1
Jan  8 09:59:17 cog1 gnome-session-binary[7218]: CRITICAL: We failed, but the fail whale is dead. Sorry....
```

Thanks for any advice!

---

