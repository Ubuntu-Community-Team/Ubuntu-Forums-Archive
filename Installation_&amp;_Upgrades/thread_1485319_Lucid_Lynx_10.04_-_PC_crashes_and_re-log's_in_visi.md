---
title: "Lucid Lynx 10.04 - PC crashes and re-log's in visiting some sites"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by rubencouto on 2010-05-16
Hello!

I've been using Ubuntu for the last year and I must say I have enjoyed it very much.

BUT, after the last upgrade (to Lucid Lynx 10.04) there has been an error that keeps showing up. What happens is that, on some sites - using Firefox - (usually sites with animations or adds using flash), the computer simply crashes down (blank screen) and after a few seconds asks me to log back in. When I do so, Firefox is off and any other application has been shut down.

Any ideas?

I went to the errors on Syslog and got this:

May 16 21:26:05 rubencouto-laptop gnome-session[9275]: WARNING: Could not parse desktop file /home/rubencouto/.config/autostart/bluetooth-applet.desktop: Ficheiro de chave não contém a chave 'Name'
May 16 21:26:05 rubencouto-laptop gnome-session[9275]: WARNING: could not read /home/rubencouto/.config/autostart/bluetooth-applet.desktop
May 16 21:26:05 rubencouto-laptop gnome-session[9275]: WARNING: Could not parse desktop file /home/rubencouto/.config/autostart/xfconf-migration-4.6.desktop: Ficheiro de chave não contém a chave 'Name'
May 16 21:26:05 rubencouto-laptop gnome-session[9275]: WARNING: could not read /home/rubencouto/.config/autostart/xfconf-migration-4.6.desktop
May 16 21:26:05 rubencouto-laptop gnome-session[9275]: WARNING: Could not parse desktop file /home/rubencouto/.config/autostart/xfce4-settings-helper-autostart.desktop: Ficheiro de chave não contém a chave 'Name'
May 16 21:26:05 rubencouto-laptop gnome-session[9275]: WARNING: could not read /home/rubencouto/.config/autostart/xfce4-settings-helper-autostart.desktop
May 16 21:26:06 rubencouto-laptop gnome-session[9275]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Ficheiro de chave não contém a chave 'Type'
May 16 21:26:06 rubencouto-laptop gnome-session[9275]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop
May 16 21:26:07 rubencouto-laptop gnome-session[9275]: WARNING: Could not launch application 'tracker-applet.desktop': Unable to start application: Falha ao executar o processo filho "tracker-applet" (Ficheiro ou directoria inexistente)
May 16 21:26:08 rubencouto-laptop gnome-session[9275]: WARNING: Could not launch application 'trackerd.desktop': Unable to start application: Falha ao executar o processo filho "/usr/lib/tracker/trackerd" (Ficheiro ou directoria inexistente)
May 16 21:26:08 rubencouto-laptop gnome-session[9275]: WARNING: Could not launch application 'xfconf-migration-4.6.desktop': Unable to start application: Falha ao executar o processo filho "/usr/lib/xfce4/xfconf-migration/xfconf-migration-4.6.pl" (Ficheiro ou directoria inexistente)
May 16 21:26:08 rubencouto-laptop gnome-session[9275]: WARNING: Could not launch application 'ubuntuone-client-applet.desktop': Unable to start application: Falha ao executar o processo filho "ubuntuone-client-applet" (Ficheiro ou directoria inexistente)
May 16 21:26:08 rubencouto-laptop gnome-session[9275]: WARNING: Could not launch application 'xfce4-settings-helper-autostart.desktop': Unable to start application: Falha ao executar o processo filho "xfce4-settings-helper" (Ficheiro ou directoria inexistente)
May 16 21:26:09 rubencouto-laptop pulseaudio[9107]: module-x11-xsmp.c: Failed to open connection to session manager: Could not open network socket
May 16 21:26:09 rubencouto-laptop pulseaudio[9107]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
May 16 21:26:14 rubencouto-laptop pulseaudio[9107]: ratelimit.c: 3 events suppressed
May 16 21:27:19 rubencouto-laptop AptDaemon: INFO: Initializing daemon

---

### Post by emanuel.b on 2010-05-16
First, I would disable compiz (assuming you use it) and try visiting the sites again. If you are not using compiz, then try disabling the flash plug-in in Firefox.

---

### Post by rubencouto on 2010-05-17
Sorry for my ignorance, but what is compiz?

I do have Shockwave Flash plugin. So I just deactivated it and tried to visit the same sites that used to crash the PC down. So far, so good!! Time and usage will tell if it really worked. Besides, navigation just got a lot faster!

Thanks for you help (for now)!

---

### Post by emanuel.b on 2010-05-18
> **rubencouto said:**
> Sorry for my ignorance, but what is compiz?

I do have Shockwave Flash plugin. So I just deactivated it and tried to visit the same sites that used to crash the PC down. So far, so good!! Time and usage will tell if it really worked. Besides, navigation just got a lot faster!

Thanks for you help (for now)!
Compiz is the desktop animation. If you have it turned on, it was probably interfering with the flash plug-in.

---

