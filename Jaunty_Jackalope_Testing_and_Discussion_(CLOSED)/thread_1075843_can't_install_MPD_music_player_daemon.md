---
title: "can't install MPD music player daemon"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ugkbunb on 2009-02-20
running xubuntu amd64 fully updated with nvidia proprietary drivers...

Is anyone else experience anything similar? By chance do you have any tips on how I could get MPD installed? Should I file a bugreport on LP?

thanks in advance

> 
$ sudo apt-get install mpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  icecast2
The following NEW packages will be installed:
  mpd
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/180kB of archives.
After this operation, 545kB of additional disk space will be used.
Selecting previously deselected package mpd.
(Reading database ... 199197 files and directories currently installed.)
Unpacking mpd (from .../mpd_0.14.2-2ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up mpd (0.14.2-2ubuntu1) ...
 * Starting Music Player Daemon mpd                                              * creating /var/lib/mpd/tag_cache... 
unable to bind port 6600: Address already in use
maybe MPD is still running?
Trace/breakpoint trap (core dumped)
                                                                         [fail]
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess post-installation script returned error exit status 133
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

It seems like it is unable to bind to port 6600 and hence is failing... anyone have any clue what would be using that port on a default jaunty installation.

---

### Post by BwackNinja on 2009-02-20
Ooh, had this problem. Probably should've bug reported it.

Anyway, in your /etc/mpd.conf, at the line that says bind_to_address, change "localhost" to "127.0.0.1" and all should be fine.

This happened in the change from mpd 0.13 to 0.14

---

### Post by ugkbunb on 2009-02-20
thank you that seems to fix it!

i went ahead and filed a bug report:
[https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/332332](https://bugs.launchpad.net/ubuntu/+source/mpd/+bug/332332)

---

