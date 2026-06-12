---
title: "GS Connect not working after 18.10 upgrade"
date: 2018-10-18
forum: Installation &amp; Upgrades
---

### Post by jbh54enwiler on 2018-10-18
After hearing that 18.10 would not provide Android integration by default, I decided to install GS Connect on my computer.  (While it was still running 18.04)  However, immediately after upgrading to 18.10, I noticed my phone (Running Android 7.1) was not showing up on screen.  After attempting to launch the Gnome extension's settings, I was greeted with this error:

***Gio.DBusError: Error calling StartServiceByName for org.gnome.Shell.Extensions.GSConnect: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.Shell.Extensions.GSConnect exited with status 1***
****
***Stack trace:***
***  [email]_init@/home/jbh/.local/share/gnome-shell/extensions/gsconnect@andyholmes.github.io/client.js[/email]:33:9***
***  [email]wrapper@resource:///org/gnome/gjs/modules/_legacy.js[/email]:82:22***
***  [email]_parent@resource:///org/gnome/gjs/modules/_legacy.js[/email]:39:12***
***  [email]_init@/home/jbh/.local/share/gnome-shell/extensions/gsconnect@andyholmes.github.io/client.js[/email]:695:9***
***  [email]wrapper@resource:///org/gnome/gjs/modules/_legacy.js[/email]:82:22***
***  [email]_init@/home/jbh/.local/share/gnome-shell/extensions/gsconnect@andyholmes.github.io/prefs.js[/email]:100:23***
***  [email]wrapper@resource:///org/gnome/gjs/modules/_legacy.js[/email]:82:22***
***  [email]buildPrefsWidget@/home/jbh/.local/share/gnome-shell/extensions/gsconnect@andyholmes.github.io/prefs.js[/email]:215:23***
***  [email]_selectExtension@resource:///org/gnome/shell/extensionPrefs/main.js[/email]:83:22***
***  [email]wrapper@resource:///org/gnome/gjs/modules/_legacy.js[/email]:82:22***
***  [email]_onCommandLine@resource:///org/gnome/shell/extensionPrefs/main.js[/email]:235:17***
***  [email]wrapper@resource:///org/gnome/gjs/modules/_legacy.js[/email]:82:22***
***  [email]main@resource:///org/gnome/shell/extensionPrefs/main.js[/email]:389:5***
***  @<main>:1:43***
  
I repeatedy re-installed GS Connect, reactivated some software updater sources I'd deactivated before upgrading (because they were causing errors such as 404 not founds and update connection failures) and it still didn't work.  I use my phone and computer simutaneously a lot and this is going to be a problem if I can't get them to play together anymore.  I know 18.10 is freshly released so there may be a few kinks but I really need this fixed.  Any solutions?

---

### Post by dino99 on 2018-10-19
There are still lot of 'extensions' not yet updated to support gnome 3.30 version. Hopes they will be very soon (before month's end)

---

