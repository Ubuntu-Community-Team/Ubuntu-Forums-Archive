---
title: "Problems with X server"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by redondos on 2006-02-19
Hi there. I'm using Ubuntu Breezy, although I mostly use KDe on this system. 

After a reboot, I couldn't log in anymore. From kdm, after typing in my credentials, the screen is blanked for a few seconds and then kdm is restarted. When using gdm instead, it tells me that my sessions lasted less than 10 seconds and shows me the login dialog again.

I can still log in from a console, that's ok. But here seems to be a problem, since I can't run some window manager initialization scripts, such as 'startkde'. Here's how it looks like.
```
redondos@refinery:~$ startkde
xsetroot:  unable to open display ''
xmodmap:  unable to open display ''
xset:  unable to open display ""
xset:  unable to open display ""
xsetroot:  unable to open display ''
startkde: Starting up...
ksplash: cannot connect to X server 
kdeinit: Aborting. $DISPLAY is not set.
Warning: connect() failed: : No such file or directory
ksmserver: cannot connect to X server 
ERROR: Couldn't attach to DCOP server!
startkde: Shutting down...
Warning: connect() failed: : No such file or directory
Error: Can't contact kdeinit!
startkde: Running shutdown scripts...
startkde: Done.
```

So I thought this was because the $DISPLAY environment variable isn't set. Should it be set in bashrc, for instance? 
Anyway, I did:
```
redondos@refinery:~$ DISPLAY=:0.0 startkde
xsetroot:  unable to open display ':0.0'
xmodmap:  unable to open display ':0.0'
xset:  unable to open display ":0.0"
xset:  unable to open display ":0.0"
xsetroot:  unable to open display ':0.0'
startkde: Starting up...
ksplash: cannot connect to X server :0.0
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-6986' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kcminit: cannot connect to X server :0.0
ksmserver: cannot connect to X server :0.0
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.

```

Which took very long, about 1 minute. What did sort of work was running the 'startx' script, which loaded the infamous X pattern background with the cross cursor for a split second then quit, so I ran `startx startkde' to see what would happen there.

What I got was my KDE desktop back, with a few glitches. For instance, kwin not always start, sometimes I have to run it manually. Another one is that konsole, and there was an X message saying 'KDE seems to be already running on this display.'. Clicking the 'okay' button there crashed kicker, then kicker restarts, and the message reappears. All this with an xterm in the background that seems to be the one where the startkde script was ran from.

My ~/.xsession-errors file:```
Xsession: X session started for redondos at Sun Feb 19 10:41:13 ART 2006
Failed to execute message bus daemon: Input/output error
EOF in dbus-launch reading address from bus daemon
Xsession: X session started for redondos at Sun Feb 19 10:44:12 ART 2006
Failed to execute message bus daemon: Input/output error
EOF in dbus-launch reading address from bus daemon
Xsession: X session started for redondos at Sun Feb 19 11:13:37 ART 2006
Failed to execute message bus daemon: Input/output error
EOF in dbus-launch reading address from bus daemon
```

By the way, there are no errors in the Xorg logs, just in case anyone wonders.

Please ask me for whatever information you think could be helpful to find the source of this problem. I don't remember installing/upgrading anything that could brake things, what I did install was postfix, and I saw a [thread](http://www.ubuntuforums.org/showthread.php?t=122247) mentioning that postfix 'ate' this guy's KDE, which I think is doubtful, but weird, since I'm having the exact same problem. That's why I posted in that thread to see what he did to fix it.

Some version numbers:
xorg: 6.8.2-77
KDE: 4:3.5.1-0ubuntu0breezy1

Anyway, any kind of help will be greatly appreciated.

--
redondos

---

### Post by redondos on 2006-02-19
The problem seemed to be related to the / partition being screwed up. A fsck 
fixed it, hopefully not momentarily. I found out what went wrong when trying 
to reinstall dbus: the partition was mounted read-only! But that happened 
during the last of many reboots the system had while I was trying to solve 
the problem.

--
redondos

---

### Post by rlklee on 2006-04-04
I have the same issue, though fsck didn't work for me.  Any other clues?

---

### Post by redondos on 2006-04-04
[QUOTE=rlklee]I have the same issue, though fsck didn't work for me.  Any other clues?[/QUOTE]
I have no idea. Are you sure your filesystem is consistant?

-- 
redondos

---

