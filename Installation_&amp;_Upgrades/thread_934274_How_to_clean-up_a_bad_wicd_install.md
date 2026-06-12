---
title: "How to clean-up a bad wicd install?"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by seantm on 2008-09-30
[B]Hi folks --- I'm having a very rough time with a wicd upgrade. I've been using it with no problems for 6 months. that was version 1.40 I believe. I was prompted to upgrade it through the upgrade manager tonight. BIG mistake! The install seemed to never take --seem to corrupt or something and then nothing was working. Ended up connecting with standard network tools on a wired connection. I've browsed forums everyone says uninstall it then --optionally-- try reinstalling it. But I'm unable to even uninstall or get rid of it. I've tried cmd line, synaptic mang. even booting to recovery mode and using the "repair dpkg" option. Nada; -I keep the same error message listed below..

Anyone know how i can really clean this thing out of my system -(Hardy 8.04)?

Thanks in advance! 

ERROR CODE OUTPUT: [/B]

[INDENT]seantm@techopia:~$ sudo apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1774kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 163957 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

---

### Post by imdano on 2008-09-30
See the thread on fixing it here: [http://wicd.sourceforge.net/punbb/viewtopic.php?pid=812](http://wicd.sourceforge.net/punbb/viewtopic.php?pid=812)

There's nothing wrong with 1.5.3, its the uninstall script for 1.4.2 that's no good.

---

### Post by kamiokande on 2008-10-02
Hi, I've read the link from the post above mine, and I'm still unclear on one point. During the upgrade process, will choosing not to keep any of the previous scripts avoid this whole problem? It seems that removing the wicd.prerm file worked for multiple posters, but is that necessary?

I ran into this problem last night and had to revert back to the previous version of wicd to get back online.

Thanks for any help!

---

### Post by imdano on 2008-10-02
It may still work if you choose not to.  You can also work around the problem by replacing the /etc/init.d/wicd that comes with 1.4.2 with the 1.5.3 version before installing (or after installing it fails, doesn't really matter).  Here's the 1.5.3 version
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          wicd
# Required-Start:    dbus
# Required-Stop:     
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts and stops Wicd
# Description:       Starts and stops Wicd, a network manager
### END INIT INFO

# Author: Adam Blackburn <compwiz18@users.sourceforge.net>
#

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="Network connection manager"
NAME=wicd
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS=""
PIDFILE=/var/run/wicd/wicd.pid
SCRIPTNAME=/etc/init.d/wicd

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Perhaps not the best idea
# but a confirmation is nice
# when starting/stopping the daemon
VERBOSE=yes

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	#   vvvv -- don't do this -- vvvv
	#   [ -e $PIDFILE ] && return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON -- \
		$DAEMON_ARGS > /dev/null 2> /dev/null\
		|| return 2
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:
```

---

### Post by kamiokande on 2008-10-02
Hey imdano, thanks for the quick response.

I tried it using this technique - I first replaced the /etc/init.d/wicd file with your text, then removed the wicd.prerm file, and finally chose to upgrade through the upgrade manager. 

Then, after attempting to run the new version of wicd using the command 'wicd-client' in the terminal, a bunch of crap came out:

```
:/var/lib/dpkg/info$ wicd-client
Loading...
Attempting to connect tray to daemon...
Success.
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 557, in <module>
    main(sys.argv)
  File "/usr/lib/wicd/wicd-client.py", line 538, in main
    tray_icon = TrayIcon(use_tray, animate)
  File "/usr/lib/wicd/wicd-client.py", line 102, in __init__
    self.icon_info = self.TrayConnectionInfo(self.tr, use_tray, animate)
  File "/usr/lib/wicd/wicd-client.py", line 121, in __init__
    self.update_tray_icon()
  File "/usr/lib/wicd/wicd-client.py", line 178, in update_tray_icon
    [state, info] = daemon.GetConnectionStatus()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/service.py", line 643, in _message_cb
    (candidate_method, parent_method) = _method_lookup(self, method_name, interface_name)
  File "/var/lib/python-support/python2.5/dbus/service.py", line 244, in _method_lookup
    raise UnknownMethodException('%s is not a valid method of interface %s' % (method_name, dbus_interface))
UnknownMethodException: org.freedesktop.DBus.Error.UnknownMethod: Unknown method: GetConnectionStatus is not a valid method of interface org.wicd.daemon

```

What am i missing here? Thanks!

---

### Post by kamiokande on 2008-10-03
Does anybody have any advice? Thanks!

---

### Post by imdano on 2008-10-03
It looks like the wrong version of the wicd daemon is running, or maybe you need a dbus restart.  Try running this ```
sudo /etc/init.d/wicd stop
sudo /etc/init.d/dbus restart
```Then try opening the GUI.  If it still doesn't work, run ```
ps -ef | grep wicd
```Kill all the processes that show up there, then run ```
sudo wicd -foe
```And post any error messages you see.

---

