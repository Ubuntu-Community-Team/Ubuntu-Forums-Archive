---
title: "Suspend + empty laptop battery equals major problems"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2009-09-22
Laptop went on suspend because of low battery, then connected power cable and it restarted, now won't load gnome-panel anymore after restart. After logging into gnome just shows blank gnome background, no gnome-panel, and only keyword combination that works is ctrl+alt+del which brings up the shutdown menu...

The error that may be the cause is:

gnome-session[2537]: WARNING: Could not launch application 'polkit-gnome-authentication-agent-1.desktop': Unable to start application: Failed to execute child process "/usr/libexec/polkit-gnome-authentication-agent-1" (No such file or directory)


Any help on this is greatly appreciated.

---

### Post by TDK800 on 2009-09-22
just installed the latest updates and now won't show any GUI

(gdm-binary:3291) : WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.20" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

WARNING **: Could not acquire name; bailing out

---

