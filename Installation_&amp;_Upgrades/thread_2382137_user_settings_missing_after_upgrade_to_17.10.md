---
title: "user settings missing after upgrade to 17.10"
date: 2018-01-09
forum: Installation &amp; Upgrades
---

### Post by rveska on 2018-01-09
Hi,

I just upgraded from ubuntu GNOME 17.04 to 17.10. After upgrading, however, I was astonished to find that certain tabs were missing from gnome-control-center, by googling around I found this [https://bugzilla.redhat.com/show_bug.cgi?id=1520431]("https://bugzilla.redhat.com/show_bug.cgi?id=1520431") redhat bug report, and my experience is similar. A newly created user account will have all features, whereas my existing account does not. I am not sure what is missing, but definitely background settings, user settings, region and language settings are missing (see screen shot). Trying to open the background tap directly from terminal gives
```
user@system:~$ gnome-control-center background 

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings; for panel gnome-background-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel; for panel gnome-datetime-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel; for panel gnome-info-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings; for panel gnome-notifications-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings; for panel gnome-online-accounts-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings; for panel gnome-privacy-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings; for panel gnome-region-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings; for panel gnome-search-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-SystemSettings; for panel gnome-sharing-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories GNOME;GTK;Settings;X-GNOME-SystemSettings;X-GNOME-Settings-Panel; for panel gnome-universal-access-panel.desktop

** (gnome-control-center:7731): WARNING **: Invalid categories System;Settings;X-GNOME-Settings-Panel;X-GNOME-SystemSettings; for panel gnome-user-accounts-panel.desktop

** (gnome-control-center:7731): WARNING **: Could not find settings panel "background"

```

---

### Post by kaptoxic on 2018-03-25
Just in case you did not solve your problems, similar issues are due to interaction with Alacarte. (See [https://bugzilla.redhat.com/show_bug.cgi?id=1520431](https://bugzilla.redhat.com/show_bug.cgi?id=1520431).)

---

