---
title: "ibus won't start after upgrade to 20.04"
date: 2020-08-31
forum: Installation &amp; Upgrades
---

### Post by delatbabel on 2020-08-31
Hi all,

This isn't a bug as such but an issue that I noted and then solved when upgrading my desktop from 18.04 to 20.04 LTS.

Prior to the upgrade I had followed the iBus installation instructions and had the iBus daemon start during login by adding /usr/bin/ibus-daemon to my application startup programs (in Startup/Shutdown in system settings in KDE, or elsewhere in GNOME). This does not work in 20.04, in order to get the iBus daemon to start and stay running you need to add the -d flag to this command.

This information might be useful for those who (like me) use Vietnamese and other foreign character input methods via the iBus helpers.

I'm adding this here because I couldn't find where else to report it in the various Ubuntu ecosystems.

Del

---

