---
title: "Some programs do not start"
date: 2016-07-13
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2016-07-13
Just installed Ubuntu 16.0.4 LTS on my Acer ES1-331-C0YK new, because I changed the HD for a 480 GB SSD.

All the programs, I have now problems with, worked fine on my first installation on this notebook.

Some are for some seconds in the taskbar, pulsate and disappear, some even do not show anything

Linux:

Font Viewer
Geogebra
GpsPrune
all other programms work

Java JTK 9

Arachnophilia
Language Tool 3,4
no other Java software tested

Windows WINE;

HP41.exe
all other works under WINE

---

### Post by Roland_Msl on 2016-07-21
I tried to reinstall Open Java 9, no effect
I tried to open Language Tool and Arachnophilia with JTK 8, no effect

How can I check, what is going on, while the started program is just blinking in the task bar?

---

### Post by Roland_Msl on 2016-07-21
I founr an article about

[https://bugs.launchpad.net/ubuntu/+source/openjdk-9/+bug/1551532](https://bugs.launchpad.net/ubuntu/+source/openjdk-9/+bug/1551532)

and tried to uninstall JTK 9

Now Language-tool 3.4 and Arachnophilia starts with JTK 8,
but same situation, nothing

What's about a hint, how to find out what happens after the program start?

---

### Post by Roland_Msl on 2016-07-21
It would have been extremely helpfull to tell me about System Log

hp.41.exe
mfc42.dll was missing. I installed at my first try much more Windows software. One of them installed mfc42.dll.
In the new installation, this DLL was missing.

Font viewer:
Jul 21 21:22:23 founder-Aspire-ES1-331 gnome-session[3087]: ** (zeitgeist-datahub:3607): CRITICAL **: string_strip: assertion 'self != NULL' failed
Jul 21 21:22:23 founder-Aspire-ES1-331 gnome-session[3087]: (zeitgeist-datahub:3607): Gtk-CRITICAL **: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Jul 21 21:22:23 founder-Aspire-ES1-331 gnome-session[3087]: ** (zeitgeist-datahub:3607): WARNING **: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0x1181140

Geogebra:
gnome-session[3087]: /usr/bin/geogebra: line 126: exec: java: not found

Arachbophilia.jar

Jul 21 21:26:14 founder-Aspire-ES1-331 gnome-session[3087]: /usr/bin/cautious-launcher: line 17: /usr/bin/java: No such file or directory
Jul 21 21:26:14 founder-Aspire-ES1-331 gnome-session[3087]: ** (zeitgeist-datahub:3607): CRITICAL **: string_strip: assertion 'self != NULL' failed
Jul 21 21:26:14 founder-Aspire-ES1-331 gnome-session[3087]: (zeitgeist-datahub:3607): Gtk-CRITICAL **: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Jul 21 21:26:14 founder-Aspire-ES1-331 gnome-session[3087]: ** (zeitgeist-datahub:3607): WARNING **: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0x117ee30

Language tool 3.4 laguagetool.jar

Jul 21 21:28:30 founder-Aspire-ES1-331 gnome-session[3087]: /usr/bin/cautious-launcher: line 17: /usr/bin/java: No such file or directory
Jul 21 21:28:31 founder-Aspire-ES1-331 gnome-session[3087]: ** (zeitgeist-datahub:3607): CRITICAL **: string_strip: assertion 'self != NULL' failed
Jul 21 21:28:31 founder-Aspire-ES1-331 gnome-session[3087]: (zeitgeist-datahub:3607): Gtk-CRITICAL **: gtk_recent_info_get_application_info: assertion 'app_name != NULL' failed
Jul 21 21:28:31 founder-Aspire-ES1-331 gnome-session[3087]: ** (zeitgeist-datahub:3607): WARNING **: recent-manager-provider.vala:106: (null) was not registered in RecentInfo item 0x117e220




GpsPrune

Strange, it starts to blink in the task bar some seconds, but nothing in the system log.

So most of the problems showed up as Java installation problems.

What now?

---

