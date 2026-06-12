---
title: "CPU Usage in idle 18-23%...?"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2010-04-09
Hi,
 i have dell mini 10v and i noticed that for last few days my cpu usage in idle (nothing is running) stays at 18-23%. Before that i had 9-10%.

Isn´t it little bit too much?

Ram stays low-at 140-170 MB 

Running Ubuntu 9.10 (gnome) on Dell mini 10v. I installed HTOP  too and it shows same usage...

---

### Post by moetunes on 2010-04-09
In htop what is the app that is using the cpu so much?

---

### Post by shaka_zulu on 2010-04-09
check system activity and see what application "eats" processor?

---

### Post by vickoxy on 2010-04-09
smfpd is only app that i do not recognize-running at about 20%.
All other: cairo-dock, conky, gnome-terminal, htop, usr/bin/X... are having very low cpu usage.

What is this **smfpd**? In conky/system there is no sign of this process-i see it only in htop...

---

### Post by vickoxy on 2010-04-09
Ok, there is something-i installed yesterday samsung drivers an found that smfpd have something to do with it:
[http://blog.rtg.in.ua/2009/09/what-is-smfpd.html](http://blog.rtg.in.ua/2009/09/what-is-smfpd.html)

Is there any way to kill this process? Should it disable my printer?

---

### Post by moetunes on 2010-04-09
htop will show its' pid - process id
exit htop and enter  -  kill -15 "pid"

---

### Post by vickoxy on 2010-04-09
> **shaka_zulu said:**
> check system activity and see what application "eats" processor?

Well, in system activity there is nothing unususal. smfpd is not there- i can see it in htop eating 15-20%

And it has something to do with samsung drivers-that is some their daemon. Any idea how to remove it or shut it down?

---

### Post by vickoxy on 2010-04-09
> **moetunes said:**
> htop will show its' pid - process id
exit htop and enter  -  kill -15 "pid"

That did, it, but after reboot-will it be there again? Is this permanent solution?

Thanks

---

### Post by vickoxy on 2010-04-09
I just printed one document. So, this smfpd is not necessary to have installed for printing ([http://blog.rtg.in.ua/2009/09/what-is-smfpd.html](http://blog.rtg.in.ua/2009/09/what-is-smfpd.html)), but can i disable this process or should i delete /usr/sbin/smfpd?

---

### Post by moetunes on 2010-04-09
> That did, it, but after reboot-will it be there again? Is this permanent solution?
is there anything in the folder
/etc/init.d
that relates to it?

---

### Post by vickoxy on 2010-04-09
> **moetunes said:**
> is there anything in the folder
/etc/init.d
that relates to it?

Yes there is:
/ets/init.d/smfpd  -some Shell-Skript

and here:

/usr/sbin/smfpd -this is some x application

On this forum i found some other places where it could be:
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

---

### Post by vickoxy on 2010-04-09
And yes-after reboot there is again this process running. 

As said, i killed it and printing is working just fine without it..

But how to remove it permanently?

Thanks for help

---

### Post by vickoxy on 2010-04-09
Well, i removed those two files:
/etc/init.d/smfpd
/usr/sbin/smfpd

Have no problems at all with printing and my cpu usage at idle is now at 6-8% again. So, i will make this thread solved.

Thanks

---

### Post by Neovos on 2010-12-01
I had this issue too. If you look at the contents of /etc/init.d/smfpd it shows you everything you need to know to "disable" it. Uncomment the "exit 0" like it says and you should be good.

```

#!/bin/sh

# smfpd is a parallel port handling daemon. It needs root privileges
# to use iopl(2), inb(2) and outb(2) system calls.
#
# smfpd uses inet domain socket, this script should be run
# after network initialization.
#
# This script is a part of Unified Linux Driver package.
# If your MFP device is not connected to LPT port, you can safely
# disable execution of this script - uncomment 'exit 0' at the next line.
exit 0

SMFPD=/usr/sbin/smfpd
test -x $SMFPD || exit 5

PATH=/usr/sbin:/sbin:/usr/bin:/bin
SMFPD=smfpd

PROCESS_PID=`ps ax | grep "[0-9]:[0-9][0-9] $SMFPD" | awk '{print $1}'`

case "$1" in
	check)
		if test -z "$PROCESS_PID"; then
			echo "Process is not running"
		else
			echo "Process $SMFPD[$PROCESS_PID] is running"
		fi
	;;
	start)
		if test -z "$PROCESS_PID"; then
			echo -n "Starting smfpd daemon ... "
			$SMFPD
			echo "done"
			$0 check
		else
			echo "Process $SMFPD[$PROCESS_PID] is already running"
		fi
	;;
	stop)
		if test -n "$PROCESS_PID"; then
			echo -n "Stopping smfpd daemon ... "
			kill -TERM $PROCESS_PID
			echo "done"
		else
			echo "Process is not running"
		fi
	;;
	restart)
		$0 stop
		sleep 1
		$0 start
	;;
	*)
		echo "Usage: $0 {check|start|stop|restart}"
		exit 1
	;;
esac

exit 0


```

---

### Post by fwahl on 2010-12-20
```
sudo update-rc.d -f smfpd remove
``` should do the trick.

---

