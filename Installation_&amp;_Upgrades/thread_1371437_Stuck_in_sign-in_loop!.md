---
title: "Stuck in sign-in loop!"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2010-01-03
Just installed Xubuntu 9.10 and it is stuck in the sign-in loop. I have restarted in restore mode and updated to fix broken packages and I am still stuck. Any ideas?

Thanks.

---

### Post by running_rabbit07 on 2010-01-03
To clarify my status, When I boot up, I get to the Login screen, where I enter my screename and password, hit enter, then it starts looking like I am going to the desktop and next thing I know it is back to the Login screen.

---

### Post by running_rabbit07 on 2010-01-03
Did a reinstall, fixed the issue.

---

### Post by ahmd6 on 2010-01-03
> **running_rabbit07 said:**
> Did a reinstall, fixed the issue.

I hope what you are saying is true. I am suffering from the same problem. I reinstalled around 5 time (I lost count) but I am still suffering. Typically things work fine for few hours and the sign-in loop appear again

---

### Post by running_rabbit07 on 2010-01-04
The only reason this may have worked for me is that I reinstalled and set to Automatically sign in at the screen name and password part of the install. 

Please be aware I am using Zenix which is a form of Ubuntu that uses XFCE, which isn't exactly the same as Xubuntu.

---

### Post by &lt;mike&gt; on 2010-01-04
i have auto signing running, but I have the same problem. I've had karmic running since it came out, but this problem didn't happen until this morning when i rebooted for the first time in ages.
Adding a new user lets me log in, but I've lost all the user-specific options I've changed.

any thoughts??

---

### Post by &lt;mike&gt; on 2010-01-04
To clarify, /var/log/syslog shows the following error each time I try to log in:
```

Jan  4 07:36:46 monet acpid: client 3023[0:0] has disconnected
Jan  4 07:36:46 monet acpid: client 3023[0:0] has disconnected
Jan  4 07:36:46 monet acpid: client connected from 3464[0:0]
Jan  4 07:36:47 monet acpid: client connected from 3464[0:0]
Jan  4 07:36:53 monet gdm-simple-greeter[3518]: WARNING: Unable to lookup user name nipplest: Success
Jan  4 07:37:49 monet acpid: client 3464[0:0] has disconnected
Jan  4 07:37:49 monet acpid: client 3464[0:0] has disconnected

```
I originally thought the problem with this might be my user name (which is 'nipplestv', not 'nipplest'), but a new user account guest12345 (same length) still logs in ok.

What other logs would be useful here??

```

cat Xorg.0.log |grep WW 

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(WW) Warning, couldn't open module type1
(EE) Failed to load module "type1" (module does not exist, 0)
(WW) Warning, couldn't open module freetype
(EE) Failed to load module "freetype" (module does not exist, 0)


```

---

### Post by &lt;mike&gt; on 2010-01-04
Ok, so I've fixed my problem.
Try looking at ~/.xsession-errors; I got:
```

cat .xsession-errors

/etc/gdm/Xsession: Beginning session setup...
04/01/2010 18:02:43 passing arg to libvncserver: -rfbauth
04/01/2010 18:02:43 passing arg to libvncserver: /home/nipplestv/.vnc/passwd
04/01/2010 18:02:43 passing arg to libvncserver: -rfbport
04/01/2010 18:02:43 passing arg to libvncserver: 5900
04/01/2010 18:02:43 x11vnc version: 0.9.3 lastmod: 2007-09-30
04/01/2010 18:02:43 Using X display :0

...
04/01/2010 18:02:43 screen setup finished.

...

/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
[COLOR=Red][B]xfce4-session: Unable to access file /home/nipplestv/.ICEauthority: Permission denied
[/B][/COLOR]
** (gnome-screensaver:7858): WARNING **: Error retrieving configuration key '/desktop/gnome/lockdown/disable_lock_screen': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Could not send message to GConf daemon: Connection was disconnected before a reply was received)

....

<username@server>~$ ls -a -l .I*
-rw------- 1 root root 18852 2010-01-04 06:36 .ICEauthority

```
...after which a 
```

<username@server>:~$ sudo chown <username> .ICEauthority
[sudo] password for <username>: <password>

```
worked perfectly.

---

