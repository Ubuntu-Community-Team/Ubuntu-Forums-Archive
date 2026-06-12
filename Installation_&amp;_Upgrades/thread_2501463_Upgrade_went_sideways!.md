---
title: "Upgrade went sideways!"
date: 2024-10-08
forum: Installation &amp; Upgrades
---

### Post by john163 on 2024-10-08
I'd upgraded from Ubuntu 22.04 to 24.04  At some point, I'd run 'apt update' and there were a ton of packages to install.  I left that as I was in the middle of something.  I let the laptop hibernate while I carried it to a different location.  At some point, I did an apt update again, and got a message about an unattended update locking.  I could find the process but a kill didn't stop it, so I rebooted.  I get booted into runlevel 3, and a whole bunch of errors like:

```
2024-10-08T08:58:25.181351-07:00 blinky systemd-xdg-autostart-generator[1716]: Exec binary 'system-config-printer-applet' does not exist: No such file or directory
2024-10-08T08:58:25.181787-07:00 blinky systemd-xdg-autostart-generator[1716]: Not generating service for XDG autostart app-print\x2dapplet@autostart.service, error parsing Exec= line: No such file or directory
```

apt upgrade shows 142 packages "held back".  I'm looking through syslog for a hint as to why I'm not getting into the GUI, but aren't finding anything.

---

### Post by john163 on 2024-10-08
I wound up fixing with:

```
[COLOR=#0C0D0E][FONT=ui-monospace]sudo apt install --reinstall ubuntu-desktop[/FONT][/COLOR]
```

---

