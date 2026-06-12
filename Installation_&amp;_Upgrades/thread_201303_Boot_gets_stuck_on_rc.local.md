---
title: "Boot gets stuck on rc.local"
date: 2006-06-21
forum: Installation &amp; Upgrades
---

### Post by wardjame on 2006-06-21
Hi All,
I did a command line upgrade from Breezy to Dapper using apt-get dist-upgrade.  Everything looked like it went ok until I rebooted into the new kernel.  After the rc.local boot message I started receiving the following messages:

INIT ID "1": Respawning too fast: Disabled for 5 minutes

With the id incrementing up to 6 then starting again.  I'm going to try to get booted back into the old kernel but any advice on how to remedy this would be much appreciated.

---

### Post by jvl on 2006-06-21
What's in the rc.local script? What does /etc/inittab look like? Does the old kernel work?

---

### Post by fishoutofwater on 2006-06-22
I'm a very newbie so I can't answer those questions jvl sorry but just to say I've had this exact issue too since upgrading from Breezy to Dapper (installed from cd) a week ago.   It is an intermittent problem tho ie does not occur everytime I boot.

---

### Post by wardjame on 2006-06-22
[QUOTE=jvl]What's in the rc.local script? What does /etc/inittab look like? Does the old kernel work?[/QUOTE]
rc.local just has the following line:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

/etc/inittab contains the following:
```
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3


```

I'm booted into the old kernel with no problems.  
Thanks for any help on this.

---

### Post by That Other Guy on 2006-07-05
Any suggestions to fix this?  I got the same problem upgrading via command line from Breezy last night.  My rc.local is the same as above, and I've tried making it non-executable as well.  It happens with the new 2.6.15 kernel as well as the previous 2.6.10-12.

I can boot so single user via the recovery mode, and can also log in off another terminal screen while it's hanging in a normal boot.

What runs after the "running local scripts" line?  It's possible that that's the real issue.  I don't get the "INIT ID 1" error posted above.

---

### Post by spaznrq on 2006-07-13
I just ran into this boot hanging problem as well.  What see after Ubuntu seems to boot up is something like this:

(after the brown Ubuntu boot screen, it goes back to the white characters on black screen and says this:)
...
Running local boot scripts              undcommand not founde[ok]

I tried rebooting several times, and got stuck at the same point, even after booting with different kernals.  I am able to do a Ctrl+Alt+F* to login and do stuff, but it just wouldn't take me to the regular Ubuntu login screen.

Finally, I was able to get to that login screen by doing a "shutdown -F now" from the Ctrl+Alt+F* screen, but I don't think this solves the problem.  It was just for me to be able to login to search for help in this forum...

---

