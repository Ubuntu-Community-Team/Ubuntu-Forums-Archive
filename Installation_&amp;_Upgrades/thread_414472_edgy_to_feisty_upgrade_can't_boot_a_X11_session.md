---
title: "edgy to feisty upgrade: can't boot a X11 session"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by q*_*p on 2007-04-19
Hi,

I just did an upgrade to feisty on my asus laptop, and now i only seem to be able to boot in recovery mode. first i thought it was a compiz or beryl problem, so i uninstalled beryl.
i can't ssh to my laptop if i try to boot it, while booting i get this:
ssh: connect to host 00.00.00.00 port 22: Connection refused
and when it's booted and i'm wachting my black screen:
ssh: connect to host 00.00.00.00 port 22: No route to host

it works when i boot in recovery mode. 

root@suhrawardi:~# startx
xauth:  creating new authority file /root/.serverauth.4571
xauth:  creating new authority file /root/.Xauthority
xauth:  creating new authority file /root/.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux suhrawardi 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 20 10:30:52 2007
(==) Using config file: "/etc/X11/xorg.conf"


does someone have an idea how to fix this problem, and whats wrong?
if you need more information, just let me know.

thanks a lot... ;-s

---

