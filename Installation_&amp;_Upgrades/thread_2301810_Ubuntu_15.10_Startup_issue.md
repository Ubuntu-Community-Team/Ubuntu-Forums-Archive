---
title: "Ubuntu 15.10 Startup issue"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by rob141 on 2015-11-05
Hello every one ;)

Here is the situation:  I had download and installed a fresh ubuntu version 15.10, 2 or 3 days ago. Evewrything seemed well untill yesterday i decided to reboot. 

Now, it boot but it does not get to the login screen. I am blocked at the purple screen were we see UBUNTU with the 5 dots under going from white to orange. The probleme is that the screen just stay at that point, it does not even get to the login screen. It does not seem to be frozen, it seem more to be waiting for a process or something like that.

I have almost nothing installed yet. I installed vlc, the fglrx drivers from synaptic package and not the priporitary one.

i installed also teamviewer and i did fallow the walkthrough to have it start before the login screen. I think that this may had cause the problem ? How can i remove this now if i cant even login to ubuntu ?? 

[COLOR=#111111][FONT=Ubuntu]TeamViewer provides a script called teamviewerd.sysv available in /opt/teamviewer/tv_bin/script. Here's an excerpt:[/FONT][/COLOR]
#!/bin/bash
#
# /etc/init.d/teamviewerd
#
# chkconfig: 2345 95 05
# description: daemon for TeamViewer
#
# processname: teamviewerd
# config: /etc/teamviewer/global.conf
# pidfile: /var/run/teamviewerd.pid

### BEGIN INIT INFO
# Provides:          teamviewerd
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Required-Start:    $all
# Required-Stop:     $local_fs $network $named
# Short-Description: TeamViewer remote control daemon
# Description:       TeamViewer remote control daemon
### END INIT INFO
[COLOR=#111111][FONT=Ubuntu]All you need to do is make sure this script runs on startup. Making sure of this is relatively simple, just copy it to /etc/init.d like so:[/FONT][/COLOR]
cd /opt/teamviewer/tv_bin/script
sudo cp teamviewerd.sysv /etc/init.d/
[COLOR=#111111][FONT=Ubuntu]Don't forget to make the script non-writable to anyone but the owner![/FONT][/COLOR]
sudo chmod 755 /etc/init.d/teamviewerd.sysv
[COLOR=#111111][FONT=Ubuntu]Then run[/FONT][/COLOR]
sudo update-rc.d teamviewerd.sysv defaults
[COLOR=#111111][FONT=Ubuntu]The service will now start automatically with each boot. If you don't feel like rebooting, you can start the service manually with:[/FONT][/COLOR]
sudo service teamviewerd.sysv start

---

### Post by rob141 on 2015-11-05
I just realised that i think i may have forgotten this part in the process:  [COLOR=#000000]sudo chmod 755 /etc/init.d/teamviewerd.sysv

Can that be the problem ?

if yes, how can i fixe this please ?[/COLOR]

---

