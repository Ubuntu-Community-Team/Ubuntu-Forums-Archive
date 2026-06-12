---
title: "mpd and sabnzdplus crashing on startup"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-02-20
Does anyone else experience this? I get the ubuntu crash icon saying that mpd and sabnzbdplus are crashing.

If i manually restart they are fine so it's something in the bootup. I'm wondering if they are trying to read from my encrypted home partition before the desktop password is put in and it's causing a problem somehow?

---

### Post by sonicb00m on 2010-02-23
anyone?

---

### Post by BwackNinja on 2010-02-23
About mpd at least, I'd check the log files in /var/log/mpd/

Also see if you can start them later, such as running 'sudo /etc/init.d/mpd start' to start mpd.

---

### Post by sonicb00m on 2010-02-25
No protocol specified
XOpenDisplay() failed
No protocol specified
XOpenDisplay() failed
No protocol specified
XOpenDisplay() failed
No protocol specified
XOpenDisplay() failed


This is the last entries in the mpd log but no time stamp so I can't be sure.

Yes, a simple restart of both services enables them.

---

### Post by sonicb00m on 2010-02-28
Seems to be the encrypted home dir. I set the permissions for mpd and sabnzbd to my user name and then reran the startup scripts in the gnome startup manager. Works ok now.

---

