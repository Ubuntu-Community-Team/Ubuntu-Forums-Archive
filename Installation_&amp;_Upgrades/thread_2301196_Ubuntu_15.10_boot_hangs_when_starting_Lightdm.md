---
title: "Ubuntu 15.10 boot hangs when starting Lightdm"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by jaredbarbre on 2015-10-31
I failed to read the release notes before upgrading to 15.10, I still had fglrx drivers installed. When rebooting after the upgrade it would hang indefinitely in the splash screen, I couldn't open a console with 'ctrl alt f1-6'. I was able to solve this by booting into recovery mode, opening up a root console purging the fglrx driver and installing the open source radeon driver. Now it hangs in this screen [http://i.imgur.com/qAzaUtu.jpg](http://i.imgur.com/qAzaUtu.jpg)
System info
memory      15GiB System memory
processor   AMD FX(tm)-8350 Eight-Core Processor
bridge      RD890 PCI to PCI bridge (external gfx0 port B)
bridge      RD890 PCI to PCI bridge (PCI express gpp port B)
display     Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
multimedia  Tahiti XT HDMI Audio [Radeon HD 7970 Series]


This is the lightdm.log
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.16.4, UID=0 PID=6021
[+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Monitoring logind for seats
[+0.00s] DEBUG: New seat added from logind: seat0
[+0.00s] DEBUG: Seat seat0: Loading properties from config section Seat:*
[+0.00s] DEBUG: Seat seat0: Starting
[+0.00s] DEBUG: Seat seat0: Creating greeter session
[+0.00s] DEBUG: Seat seat0: Creating display server of type x
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: Seat seat0: Starting local X display on VT 7
[+0.00s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.00s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.00s] DEBUG: DisplayServer x-0: Launching X Server
[+0.01s] DEBUG: Launching process 6033: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1001 added
[+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.28s] DEBUG: Got signal 10 from process 6033
[+0.28s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+0.28s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+0.28s] DEBUG: Seat seat0: Display server ready, starting session authentication
[+0.28s] DEBUG: Session pid=6149: Started with service 'lightdm-greeter', username 'lightdm'
[+0.29s] DEBUG: Session pid=6149: Authentication complete with return value 0: Success
[+0.29s] DEBUG: Seat seat0: Session authenticated, running command
[+0.29s] DEBUG: Session pid=6149: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+0.29s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+0.29s] DEBUG: Session pid=6149: Logging to /var/log/lightdm/x-0-greeter.log
[+0.31s] DEBUG: Activating VT 7
[+0.31s] DEBUG: Activating login1 session c15
[+0.31s] DEBUG: Seat seat0 changes active session to c15
[+0.31s] DEBUG: Session c15 is already active
[+0.31s] DEBUG: Session pid=6149: Greeter closed communication channel
[+0.31s] DEBUG: Session pid=6149: Exited with return value 1
[+0.31s] DEBUG: Seat seat0: Session stopped
[+0.31s] DEBUG: Seat seat0: Stopping; failed to start a greeter
[+0.31s] DEBUG: Seat seat0: Stopping
[+0.31s] DEBUG: Seat seat0: Stopping display server
[+0.31s] DEBUG: Sending signal 15 to process 6033
[+0.76s] DEBUG: Process 6033 exited with return value 0
[+0.76s] DEBUG: DisplayServer x-0: X server stopped
[+0.76s] DEBUG: Releasing VT 7
[+0.76s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
[+0.76s] DEBUG: Seat seat0: Display server stopped
[+0.76s] DEBUG: Seat seat0: Stopped
[+0.76s] DEBUG: Required seat has stopped
[+0.76s] DEBUG: Stopping display manager
[+0.76s] DEBUG: Display manager stopped
[+0.76s] DEBUG: Stopping daemon
[+0.76s] DEBUG: Exiting with return value 1
........................................................................................................

The x-0-greeter.log
error writing X authority: Failed to open X authority /var/lib/lightdm/.Xauthority: No such file or directory

---

### Post by jaredbarbre on 2015-11-01
Found the solution here [http://askubuntu.com/questions/692577/ubuntu-15-10-boot-hangs-when-starting-lightdm](http://askubuntu.com/questions/692577/ubuntu-15-10-boot-hangs-when-starting-lightdm)

---

