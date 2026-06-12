---
title: "gnome-shell / mutter fails to start, goes back to gdm"
date: 2019-05-27
forum: Installation &amp; Upgrades
---

### Post by nachokb2 on 2019-05-27
Upgraded from 18.10 to 19.04. On boot GDM starts normally, and after I enter my password it fails to start GNOME. It goes back to GDM
This is an Nvidia Optimus laptop. I ran Dingo from USB and installed it into a test partition. It recognizes everything (uses nouveau instead of the Nvidia blob).

Log says:

```
    WARNING: App 'org.gnome.Shell.desktop' exited with code 1
    Unrecoverable failure in required component org.gnome.Shell.desktop
    WARNING: App 'org.gnome.Shell.desktop'  respawning too quickly
    CRITICAL: We failed, but the fail whale is dead. Sorry...
```

Both mutter sessions using Xorg and Wayland fail the same way (and both Gnome and Unity, same thing). The old metacity "GNOME Flashback" starts ok (but then indicator-datetime-service eats all CPU and memory and won't stop respawning if I kill it; I managed to mv the binary so it's barely usable now).

Tried using lightdm instead of GDM. It fails the same way.

Tried reinstalling gnome-session package. Nothing changed.

All logs obtained via journalct -xe.

Any advice on how to debug this thing will be welcome.

Later, I realised that I had inadvertently enabled the "proposed" repository (in my cosmic install). Downgraded gnome-shell ("3.32.1-1ubuntu1~19.04.1" to "3.32.0+git20190410-1ubuntu1"), mutter and other packages (using pinning priority), but the problem reamins exactly the same.

This is a longer excerpt from the logs (using Budgie now):


```
may 27 02:04:56 valinor gnome-shell[3334]: JS ERROR: TypeError: b.location.get_timezone(...) is null
                                           _clocksChanged/<@resource:///org/gnome/shell/ui/dateMenu.js:127:20
                                           [email]_clocksChanged@resource:///org/gnome/shell/ui/dateMenu.js[/email]:125:9
                                           [email]_connectHandler@resource:///org/gnome/shell/misc/util.js[/email]:472:9
                                           [email]watchSetting@resource:///org/gnome/shell/misc/util.js[/email]:463:9
                                           [email]WorldClocksSection@resource:///org/gnome/shell/ui/dateMenu.js[/email]:102:9
                                           [email]_init@resource:///org/gnome/shell/ui/dateMenu.js[/email]:530:28
                                           [email]_ensureIndicator@resource:///org/gnome/shell/ui/panel.js[/email]:1116:25
                                           [email]_updateBox@resource:///org/gnome/shell/ui/panel.js[/email]:1127:29
                                           [email]_updatePanel@resource:///org/gnome/shell/ui/panel.js[/email]:1072:9
                                           [email]_init@resource:///org/gnome/shell/ui/panel.js[/email]:873:9
                                           [email]_initializeUI@resource:///org/gnome/shell/ui/main.js[/email]:178:13
                                           [email]start@resource:///org/gnome/shell/ui/main.js[/email]:127:5
                                           @<main>:1:31
may 27 02:04:56 valinor gnome-shell[3334]: Execution of main.js threw exception: Script <main> threw an exception
may 27 02:04:56 valinor gnome-shell[3334]: Attempting to call back into JSAPI during the sweeping phase of GC. This is most likely caused by not destroyin
may 27 02:04:56 valinor org.gnome.Shell.desktop[3334]: == Stack trace for context 0x55852aa8a230 ==
may 27 02:04:56 valinor gnome-shell[3334]: The offending signal was destroy on Gjs_DateMenuButton 0x55852bdbd810.
may 27 02:04:56 valinor gnome-session[3131]: gnome-session-binary[3131]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
may 27 02:04:56 valinor gnome-session[3131]: gnome-session-binary[3131]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
may 27 02:04:56 valinor gnome-session-binary[3131]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
may 27 02:04:56 valinor gnome-session-binary[3131]: Unrecoverable failure in required component org.gnome.Shell.desktop
may 27 02:04:56 valinor gnome-session[3131]: gnome-session-binary[3131]: CRITICAL: We failed, but the fail whale is dead. Sorry....
may 27 02:04:56 valinor gnome-session-binary[3131]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
may 27 02:04:56 valinor gnome-session-binary[3131]: CRITICAL: We failed, but the fail whale is dead. Sorry....
may 27 02:04:56 valinor gdm-x-session[3117]: session exited with status 1
may 27 02:04:56 valinor at-spi-bus-launcher[3250]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
may 27 02:04:56 valinor at-spi-bus-launcher[3250]:       after 21 requests (21 known processed) with 0 events remaining.
may 27 02:04:56 valinor ibus-daemon[3309]: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). See the d
may 27 02:04:56 valinor /usr/lib/gdm3/gdm-x-session[3117]: (**) Option "fd" "26"
-- nachokb

```

---

