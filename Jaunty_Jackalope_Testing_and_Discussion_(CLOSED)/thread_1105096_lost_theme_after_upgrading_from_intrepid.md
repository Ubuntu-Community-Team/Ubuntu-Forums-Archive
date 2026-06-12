---
title: "lost theme after upgrading from intrepid"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forcotton on 2009-03-24
Hi,
I just upgraded from intrepid by changing the the repositories and apt-get update + apt-get dist-upgrade. Everything seems fine except the theme is lost - all applications use the default (ugly, too beveled) theme. 

When I open the appearance dialog, it says "Unable to start the settings manager 'gnome-settings-daemon', without the GNOME setting manager running blah blah..." Then it shows up with the correct theme, but all other window are still using the default theme.

I have checked (before I start the appearance dialog) that gnome-settings-daemon is running. When I try to start a new one from command line, it will complain:
```
** (gnome-settings-daemon:4355): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:4355): WARNING **: Could not acquire name

```
Any one experience the same problem?

---

### Post by forcotton on 2009-03-24
solved by replacing ~/.gnome2 directory. Not sure which file caused the problem.

---

