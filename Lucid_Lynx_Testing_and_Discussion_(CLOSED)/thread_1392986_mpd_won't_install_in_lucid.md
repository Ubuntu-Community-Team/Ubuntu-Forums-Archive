---
title: "mpd won't install in lucid"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by malachi1990 on 2010-01-28
Hi!

I was trying to setup mpd on lucid (64 bit), and I hit this in the installation:

Setting up mpd (0.15.4-1ubuntu3) ...
 * Starting Music Player Daemon mpd                                             
mkdir: cannot create directory `~/.mpd': No such file or directory
chown: cannot access `~/.mpd': No such file or directory
 * creating ~/.mpd/database... 
log: problem opening log file "/root/.mpd/log" (config line 37) for writing
Trace/breakpoint trap (core dumped)
                                                                   [fail]
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess installed post-installation script returned error exit status 133
Errors were encountered while processing:
 mpd


After this, I tried creating the ~/.mpd directory, but to no avail, as I get the exact same message.

Thank you for your time.

---

### Post by Reiger on 2010-01-28
Worth looking into: try:
```

sudo mkdir -p /root/.mpd/
sudo chmod 755 /root/.mpd/

```

I am guessing that the issue is caused by the fact that the install script is run as root and thus that ~ expands to the home directory of root which is /root/

---

### Post by malachi1990 on 2010-02-02
Thanks, that got it to install.  Now it's running into a million other issues, but I don't have the time to debud it at the moment.

---

