---
title: "apt-get help"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by TCSnyder on 2008-10-09
I was installing dansguardian and the gui tool for it and apt-get stopped working. i restarted my computer after about 10 min ( probably caused the problem) and now i cannot remove dansguardian and it doesnt work. 

sudo apt-get remove dansguardian 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  clamav clamav-freshclam clamav-base libclamav2 libclamav3 libgmp3c2
  libesmtp5
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dansguardian
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1536kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing dansguardian (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

then i  cant install it again
Synaptic' message is cut off. i try to uninstall it and it says 

"E: dansguardian: Package is in a very bad inconsistent state - you should"

but the details of Synaptic tell me to reinstall it before trying to remove it, but i cannot select reinstall in synaptic. 

it has an update but it fails and says to reinstall it. so my best guess was to

sudo apt-get install dansguardian
```
sudo apt-get install dansguardian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclamav2
Use 'apt-get autoremove' to remove them.
Suggested packages:
  squid
The following packages will be upgraded:
  dansguardian
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/295kB of archives.
After this operation, 16.4kB of additional disk space will be used.
Selecting previously deselected package dansguardian.
(Reading database ... 150938 files and directories currently installed.)
Preparing to replace dansguardian 2.8.0.6-antivirus-6.4.4.1-4build1~gutsy2 (using .../dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1_i386.deb) ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Starting DansGuardian: LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

it also does not show up in the broken libraries. i dunno what to do.

---

### Post by TCSnyder on 2008-10-09
i am going to try downloading from a dansguardian.tar.gz instead of Synaptic. i installed it from synaptic so i dont know whats wrong

---

### Post by iaculallad on 2008-10-09
Try running the command below on your terminal:

```
sudo apt-get -f install
```

---

### Post by TCSnyder on 2008-10-09
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclamav2
Use 'apt-get autoremove' to remove them.
Suggested packages:
  squid
The following packages will be upgraded:
  dansguardian
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/295kB of archives.
After this operation, 16.4kB of additional disk space will be used.
(Reading database ... 150938 files and directories currently installed.)
Preparing to replace dansguardian 2.8.0.6-antivirus-6.4.4.1-4build1~gutsy2 (using .../dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1_i386.deb) ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Starting DansGuardian: Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dansguardian_2.8.0.6-antivirus-6.4.4.1-4build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

nope that didnt work neither did "sudo apt-get -f remove"

---

### Post by TCSnyder on 2008-10-09
Can i just find where dansguardian is and delete it maually. 
i could find it with the whereis command. would it be bad to just delete all instances of it

---

### Post by rishabh on 2008-10-09
> **TCSnyder said:**
> Can i just find where dansguardian is and delete it maually. 
i could find it with the whereis command. would it be bad to just delete all instances of it

Don't try all those silly things ;)
Try this instead:
```
sudo dpkg --remove --force-remove-reinstreq dansguardian
```

---

### Post by TCSnyder on 2008-10-09
```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 150937 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--remove):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: Error connecting to parent proxy
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dansguardian

```

---

### Post by sarv on 2008-10-09
hey mates, just today i got started with ubutu and i was not able to install flash nor java for videos online...

so if you may, help me with that problem.

thank you

your new friend Sarv

---

### Post by rishabh on 2008-10-09
Since you aborted it halfway, it seems to be missing some files.
You might want to try this to fool it:
```
sudo echo  > /usr/local/apps/parental-control/./dansguardian_log.pl
```

Meanwhile, I'll try and get you a working copy of the init.d script that keeps failing to stop.

---

### Post by rishabh on 2008-10-09
This is /etc/init.d/dansguardian
```
#! /bin/sh
# Startup script for dansguardian
#
# description: A web content filtering plugin for web \
#              proxies, developed to filter using lists of \
#              banned phrases, MIME types, filename \
#              extensions and PICS labling.
# processname: dansguardian
# pidfile: /var/run/dansguardian.pid
# config: /etc/dansguardian/dansguardian.conf
### BEGIN INIT INFO
# Provides:          dansguardian
# Required-Start:    $network $syslog
# Required-Stop:     $network 
# Default-Start:     2 3 5 
# Default-Stop:      0 6 
# Description: Starts dansguardian content proxy 
# short-description: dansguardian configuration
### END INIT INFO

#include lsb functions
. /lib/lsb/init-functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/dansguardian
NAME=dansguardian
DESC="DansGuardian"

CONFFILELOCATION=/etc/dansguardian/
#BINARYLOCATION=/usr/sbin/
#PIDDIR=/var/run/

grep -q ^UNCONFIGURED ${CONFFILELOCATION}dansguardian.conf && {
cat <<EOF
        DansGuardian has not been configured!
        Please edit ${CONFFILELOCATION}dansguardian.conf manually then rerun
        this script.
EOF
exit; }

test -x $DAEMON || exit 0
test -f $CONFIG || exit 0

set -e

case "$1" in
  start)
	log_daemon_msg "Starting $DESC" "$NAME"
	start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
		--exec $DAEMON || log_end_msg 1
	log_end_msg 0
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	start-stop-daemon --stop --quiet --retry 15 --oknodo --pidfile /var/run/$NAME.pid \
		--exec $DAEMON || log_end_msg 1
	log_end_msg 0
	;;
  reload)
	log_action_begin_msg "Reloading $DESC configuration..."
	echo "Reloading $DESC configuration files."
	start-stop-daemon --stop --signal 1 --quiet --pidfile \
		/var/run/$NAME.pid --exec $DAEMON || log_action_end_msg 1
	log_action_end_msg 0
  	;;
  restart|force-reload)
	#
	#	If the "reload" option is implemented, move the "force-reload"
	#	option to the "reload" entry above. If not, "force-reload" is
	#	just the same as "restart".
	#
	echo -n "Restarting $DESC: "
	log_daemon_msg "Restarting $DESC: "
	start-stop-daemon --stop --quiet --retry 15 --oknodo --pidfile \
		/var/run/$NAME.pid --exec $DAEMON || log_end_msg 1
	start-stop-daemon --start --quiet --pidfile \
		/var/run/$NAME.pid --exec $DAEMON || log_end_msg 1
	log_end_msg 0
	;;
  *)
	N=/etc/init.d/$NAME
	# echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	log_action_msg "Usage: $N {start|stop|restart|force-reload}" >&2
	exit 1
	;;
esac

exit 0
```

Try replacing your copy of the file with the one I've provided.
If the number of deformed files is small, I can give you copies of those files, with which you can replace (patch it, so to speak) the broken files you have.
(Unless anyone else has a better idea, of course :P)

---

### Post by TCSnyder on 2008-10-09
well that didn't work either. my code in the file was the same as yours but i copied it anyways and it still doesn't work. i honestly justwanna get rid of this

---

### Post by TCSnyder on 2008-10-09
ok for future reference. i moved the file "/usr/sbin/dansguardian" ( i guess you could delete it but i just moved it to be safe)
```
sudo mv /usr/sbin/dansguardian ~/Desktop
```
 the i removed it. and it seems to have worked.
```
sudo apt-get remove dansguardian
```

thanks for all the replies

---

### Post by dave_a on 2009-05-17
It looks like when dansguardian is initially installed, 
 
This line:
UNCONFIGURED - Please remove this line after configuration

 in the file:
/etc/dansguardian/dansguardian.conf 
 
needs to be removed, so the software knows that you have looked at the configuration.

---

