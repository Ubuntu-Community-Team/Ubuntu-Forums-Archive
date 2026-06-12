---
title: "LightDM does not start automatically after 12.04.03 lts / kde-plasma upgrade"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by vivienneanthony on 2013-09-09
Hello

I wonder if anyone knows the problem or solution. I upgraded to the latest version of 12.04 LTS (12.04.03). After the upgrade, the LightDM stopped working which uses the unity greeter. Previously, there was no delay from bootup to the desktop. Now I'm having problems and I put a temporary sleep command before LightDM is executed.

My system is new I-2700k, Asus P77 motherboard, 16 gigs ram, Evga gtx 560ti, and Ubuntu installed on a SD with over 16 gigs of free space.  So, I shouldn't need  a sleep command before executing lightdm.

When I go to the command line and do a > sudo lightdm.  It starts. It's not starting fully at boot and it shows Ubuntu switching to low graphics mode or exit to console.

Vivienne

LightDM Log
------------
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1115
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: Activating VT 7
[+0.00s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 1151: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[B][+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Stopping Plymouth, no displays replace it[/B]
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.33s] DEBUG: Process 1151 exited with return value 1
[+0.33s] DEBUG: X server stopped
[+0.33s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.33s] DEBUG: Releasing VT 7
[+0.33s] DEBUG: Display server stopped
[+0.33s] DEBUG: Stopping display
[+0.33s] DEBUG: Display stopped
[+0.33s] DEBUG: Stopping X local seat, failed to start a display
[+0.33s] DEBUG: Stopping seat
[+0.33s] DEBUG: Seat stopped
[+0.33s] DEBUG: Required seat has stopped
[+0.33s] DEBUG: Stopping display manager
[+0.33s] DEBUG: Display manager stopped
[+0.33s] DEBUG: Stopping daemon
[+0.33s] DEBUG: Exiting with return value 1

---

