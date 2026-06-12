---
title: "Console-kit-daemon"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gyterpena on 2008-09-27
Hi I'm having some problems with console-kit-daemon syslog is spammed with this
Sep 27 02:20:05 epia-server console-kit-daemon[8710]: WARNING: Unable to open directory /etc/ConsoleKit/run-session.d: Error opening directory '/etc/ConsoleKit/run-session.d': $
Sep 27 02:20:05 epia-server console-kit-daemon[8710]: WARNING: Unable to open directory /usr/lib/ConsoleKit/run-session.d: Error opening directory '/usr/lib/ConsoleKit/run-sess$
Sep 27 02:20:05 epia-server console-kit-daemon[8710]: WARNING: Cannot create file /var/run/ConsoleKit/database~: Too many open files
Sep 27 02:20:05 epia-server console-kit-daemon[8710]: WARNING: Cannot unlink /var/run/ConsoleKit/database: No such file or directory
Sep 27 02:20:05 epia-server console-kit-daemon[8710]: WARNING: Cannot create file /var/run/ConsoleKit/database~: Too many open files
Sep 27 02:20:05 epia-server console-kit-daemon[8710]: WARNING: Cannot unlink /var/run/ConsoleKit/database: No such file or directory

I can't reproduce it as it happens randomly and if I don't notice it in time it gets  worse and leads to total system lock up. Even worse when I do hard reboot, system wont boot at all(freezes before BIOS). I have to clear CMOS set it back and then boot.
Shortly before lock up there is this line
Sep 27 09:59:02 epia-server console-kit-daemon[8710]: WARNING: Couldn't read /proc/21123/environ: Failed to open file '/proc/21123/environ': Too many open files

Thanks Peter

---

### Post by vikrant82 on 2008-09-27
I can confirm this happening in here with exactly same logs.

I can mount and eject my ipod when I start my system, but as time passes, I cannot anymore. If I try, I get these lines in my system log as well.

Eventually as time passes these logs become more and more.

How about a bug report ?

---

### Post by m.hataj on 2008-09-28
here too.
i cannot shutdown the system.

```
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Unable to open directory /etc/ConsoleKit/run-session.d: Error opening directory '/etc/ConsoleKit/run-session.d': Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Unable to open directory /usr/lib/ConsoleKit/run-session.d: Error opening directory '/usr/lib/ConsoleKit/run-session.d': Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Cannot create file /var/run/ConsoleKit/database~: Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Cannot unlink /var/run/ConsoleKit/database: No such file or directory 
Sep 28 08:55:01 corona /USR/SBIN/CRON[15629]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Unable to open directory /etc/ConsoleKit/run-session.d: Error opening directory '/etc/ConsoleKit/run-session.d': Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Unable to open directory /usr/lib/ConsoleKit/run-session.d: Error opening directory '/usr/lib/ConsoleKit/run-session.d': Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Cannot create file /var/run/ConsoleKit/database~: Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Cannot unlink /var/run/ConsoleKit/database: No such file or directory 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Cannot create file /var/run/ConsoleKit/database~: Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Cannot unlink /var/run/ConsoleKit/database: No such file or directory 
Sep 28 08:55:01 corona console-kit-daemon[12351]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Couldn't read /proc/13988/environ: Failed to open file '/proc/13988/environ': Too many open files 
Sep 28 08:55:01 corona gnome-session[13988]: WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Couldn't read /proc/13988/environ: Failed to open file '/proc/13988/environ': Too many open files 
Sep 28 08:55:01 corona console-kit-daemon[12351]: WARNING: Couldn't read /proc/13988/environ: Failed to open file '/proc/13988/environ': Too many open files 
```

---

### Post by ispiked on 2008-10-04
There were a few [Launchpad bugs](https://launchpad.net/ubuntu/+source/consolekit) related to this issue that are now fixed. Hopefully the two patches will resolve the issue.

---

