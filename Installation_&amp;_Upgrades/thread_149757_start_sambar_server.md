---
title: "start sambar server"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by aabunds on 2006-03-24
After haveing user windows for several years, i have decidet to try linux.8)  Until now i have managed to handle the differences myself. but now i need to get my sambar server started at boot. I have found a script, but it is not compatible with ubuntu. Can anyone help me with to adjust it? Sambar is a standalone server and is practically plug and play.

the script:
#! /bin/sh
#
# sambar          Start/Stop Sambar Server.
#
# processname: server
# config: <SambarInstDir>/config/*

INITD=/etc/rc.d/init.d
. $INITD/functions

. /etc/sysconfig/network

# Check that networking is up.
# Pretty much need it for postmaster.
[ "${NETWORKING}" = "no" ] && exit 0
  
RETVAL=0
PROGDIR=/home/tod/ver6/sambar-linux/bin

start() {
	echo -n $"Starting $PROGDIR: server"
	cd $PROGDIR; ./server &
	RETVAL=$?
	echo
	[ $RETVAL -eq 0 ] && touch /var/lock/subsys/sambar
	return $RETVAL
}

stop() {
	echo -n $"Stopping $PROGDIR: server"
	killproc watcher
	killproc server
	RETVAL=$?
	echo
	[ $RETVAL -eq 0 ] && rm -f /var/lock/subsys/sambar
	return $RETVAL
}	

restart() {
	stop
	start
}

# See how we were called.
case "$1" in
  start)
        start
        ;;
  stop)
        stop
        ;;
  status)
        status postmaster
        ;;
  restart)
        restart
        ;;
  *)
        echo $"Usage: $0 {start|stop|restart}"
        exit 1
esac

exit 0

---

### Post by Duffy on 2006-11-16
I have sambar running now, but cannot get the script to work mainly because the directions were written for Red Hat, and there are too many differences to figure out. I have it running and can start from Super User, but cannot get the script to work when system starts. Did you ever figure this out? I could use some help.

Thanks,

Duffy

---

### Post by Duffy on 2007-02-15
Finally got an answer to this issue. You can find it here:

[http://www.ubuntuforums.org/showthread.php?t=333317](http://www.ubuntuforums.org/showthread.php?t=333317)

---

