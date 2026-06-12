---
title: "&quot;su - &lt;user&gt; -c &lt;cmd&gt;&quot; fails during runlevel 2 startup in a /etc/init.d script"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Frickelton on 2009-11-26
After upgrading to 9.04 the "su - <user> -c <cmd>" in one of my /etc/init.d/ scripts fails during runlevel 2 startup. It works fine if I run it manually as root after logging in - just not during runlevel 2. Any Ideas?

Also, I seem to recollect that in 8.10 the default runlevel was 3.

Thanks for looking.

---

### Post by lswb on 2009-11-26
Perhaps some services necessary for your script have not been started yet in the 9.04 init sequence compared to your previous installation. Also it may be a simple path or environment problem. What is the actual command that is failing?

---

### Post by Frickelton on 2009-11-26
The script starts in 2 3 4 5 and stops in 0 1 6.

It does touch /root/test.turd, but strangely never touches /home/otheruser1/test.turd (it's the same for all accounts).

$ cat /etc/init.d/test
#!/bin/sh
#
### BEGIN INIT INFO
# Provides:       test
# Required-Start:
# Required-Stop: 
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Description:    Run test of su
### END INIT INFO

case "$1" in start)
        # Start daemons.
    /usr/bin/touch /root/test.turd
    su - otheruser1 -c "/usr/bin/touch /home/otheruser1/test.turd" &
    ;;
    stop)
        # Stop daemons.
        echo
        ;;
        *)
        echo "Usage: test {start|stop}"
        exit 1
        esac

        exit 0

---

### Post by lswb on 2009-11-26
Is your /home on a separate partition or drive, and has it been mounted when the script runs?

To help diagnose, you can save any output or errors from the touch command to a file:

```

su - otheruser1 -c "/usr/bin/touch /home/otheruser1/test.turd >/path/to/logfile 2>&1" &

```

---

### Post by Frickelton on 2009-11-26
Accounts are on a separate partition:
```

/dev/sda6             19524768   5553820  13970948  29% /
/dev/sda5               139985     57696     75062  44% /boot
/dev/sda8             59098332  35059236  24039096  60% /home

```I've changed the script:
```

case "$1" in start)
    # Start daemons.
    ls -l /home/otheruser1 2>&1 > /root/test.turd
    su - otheruser1 -c "/usr/bin/touch /root/test2.turd" &
    su - otheruser1 -c "/usr/bin/touch /home/otheruser1/test.turd 2>&1 > /root/test.log" &
    ;;

```Interestingly, /root/test2.turd, /home/otheruser1/test.turd and /root/test.log are untouched, but /root/test.turd has the ls:
```

$ cat /root/test.turd 
total 0
lrwxrwxrwx 1 otheruser1 otheruser1 26 Nov 13 12:33 Examples -> /usr/share/example-content
drwxr-xr-x 3 otheruser1 otheruser1 35 Nov 13 12:40 workspaces

```

---

### Post by lswb on 2009-11-26
I'm thinking that since the touch command is working via "su - otheruser1" that it will not have permission to write to a logfile owned by root. Have you checked the ordering of your initscripts and ensured that /home is mounted before your script runs? Can you temporarily umount /home or and see if the /home directory where it is mounted contains contains the missing files?

---

### Post by Frickelton on 2009-11-26
The "ls -l /home/otheruser1 2>&1 > /root/test.turd" works, so the account must be mounted.

It's commands in "su - otheruser1 -c <cmd>" that are not running. I changed the permission on the files in /root so they could be written from ~otheruser1 (tested by running the script manually after login).

The test script is S20, so the last thing to run.

---

### Post by Frickelton on 2009-11-26
Capturing the output for the su commands reveals nothing unfortunately:
```

case "$1" in start)
        # Start daemons.
    ls -l /home/otheruser1 2>&1 > /root/test.turd
    su - otheruser1 -c "/usr/bin/touch /root/test2.turd" 2>&1 > /root/test2.log &
    su - otheruser1 -c "/usr/bin/touch /home/otheruser1/test.turd 2>&1 > /root/test.log" 2>&1 > /root/test3.log &
    ;;

```The files are empty:
```

-rw-r--r-- 1 root root    0 2009-11-26 21:52 test2.log
-rw-r--r-- 1 root root    0 2009-11-26 21:52 test3.log

```

---

