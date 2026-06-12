---
title: "VNC installation trouble.."
date: 2022-12-15
forum: Installation &amp; Upgrades
---

### Post by stephenryan8 on 2022-12-15
Hello, first time poster, long time user. Apologies in advance for any bumblings..

I've recently installed 22.04 (then upgraded to 22.10) on a standalone machine
that I'm going to use for a standalone dhcp server to make up for the utter horrible
dhcp situation on my NETGEAR CAX30 cablerouter.
I got the dhcp service working and added a Glass frontend as a service. All this works great
and my last adjustment is to make the machine run headless using vnc to
access it so I can stow it in my machine cabinet.

I have tried using tigervnc, x11vnc, and tightvnc and all three have the following problem.

-the install works fine with no issues.
-setting the password (when required) works

When I try a test run of the server from the command line I get the following error:

$vncserver :1
A X11 server is already running for display :1 on machine dhcpserver.
$

I've tried switching between GNOME, Ubuntu, Ubuntu with Xorg... same.
I've searched here and on the web but can't find any reference to this message.
There is some reference to duplicate vnc servers running but not the X11 conflict.

I thought the vnc part would be easy compared to dhcp and glass but I've spent
way more time trying to figure this out.

Thanks in advance for any help.

---

### Post by stephenryan8 on 2022-12-15
Also... This problem existed on 22.04 and I upgraded thinking it might help.
Sorry for the lack of log file or related info. I'm accessing the forum on a different
machine and the lack of vnc makes it tough to cut/paste. I also am not sure where
to look for the log information.
THX

---

### Post by ActionParsnip on 2022-12-16
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)
May help

---

### Post by stephenryan8 on 2022-12-16
AP, Thanks for the reply. I followed the post you suggested. The install was clean.
When I ran vncserver the first time I got the following:

sryan@dhcpserver:~$ vncserver

You will require a password to access your desktops.

Password:
Verify:
Would you like to enter a view-only password (y/n)? n
A view-only password is not used

Warning: dhcpserver:1 is taken because of /tmp/.X1-lock
Remove this file if there is no X server dhcpserver:1

New 'X' desktop is dhcpserver:2

Creating default startup script /home/sryan/.vnc/xstartup
Starting applications specified in /home/sryan/.vnc/xstartup
Log file is /home/sryan/.vnc/dhcpserver:2.log

sryan@dhcpserver:~$ 

--------------

I expect that this is what the other vnc servers were complaining about as well.
This time the server startup was smart enought to try the next instance (2). The
following was in dhcpserver:2.log

16/12/22 08:24:57 Xvnc version TightVNC-1.3.10
16/12/22 08:24:57 Copyright (C) 2000-2009 TightVNC Group
16/12/22 08:24:57 Copyright (C) 1999 AT&T Laboratories Cambridge
16/12/22 08:24:57 All Rights Reserved.
16/12/22 08:24:57 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
16/12/22 08:24:57 Desktop name 'X' (dhcpserver:2)
16/12/22 08:24:57 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
16/12/22 08:24:57 Listening for VNC connections on TCP port 5902
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/sryan/.Xresources'

------------

I can get a vnc client to connect to the port and verify my password.
Then I get a grey X desktop with nothing else. I want VNC to run in
non-X mode.
Do you know:
-what is causing the :1 interface to be X11?
-how to get vnc to use the bitmap mode instead of X11 mode?
Thanks again.

---

