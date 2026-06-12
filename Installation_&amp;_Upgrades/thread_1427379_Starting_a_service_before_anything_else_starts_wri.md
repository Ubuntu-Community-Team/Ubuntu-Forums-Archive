---
title: "Starting a service before anything else starts writing the /var/log"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by baerwin on 2010-03-11
Hello all, and thanks ahead of time for the help.

I am trying to install ramlog on Ubuntu 9.10.  I have compiled it from source and followed to instructions for installing it as a service.  Here are the commands I ran to install it:

/usr/sbin/update-rc.d ramlog start 2 2 3 4 5 . stop 99 0 1 6 . 
/usr/sbin/update-rc.d -f sysklogd remove
/usr/sbin/update-rc.d sysklogd start 10 2 3 4 5 . stop 90 0 1 6 .

I do an `ls` in /etc/rc2.d and see S02ramlog before anything else.  Okay, all is fine.  Now I reboot my machine.

ramlog has not been started.  Hmm, interesting I wonder, so I examine /var/log/ramlog and see the following line:

Wed Mar 10 21:41:13 PST 2010 Starting ramlog: Error: /var/log is already in use...  [fail]

Ok, my next step is to determine what services are already using /var/log.  So since /etc/init.d/ramlog is just a script, I insert: /etc/init.d/ramlog teststartstop > /tmp/teststartstop

at line 268.  Running this will tell you what services are using /var/log.  Now I reboot again, then examine the contents of /tmp/teststartstop and find:

The list of open files: (You need to close below daemons if you want to start/stop ramlog manually)

COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
console-k 704 root    9w   REG    8,1    19126 137363 /var/log/ConsoleKit/history
gdm-simpl 908 root    1u   REG    8,1        0 131273 /var/log/gdm/:0-slave.log
gdm-simpl 908 root    2u   REG    8,1        0 131273 /var/log/gdm/:0-slave.log
Xorg      927 root    0r   REG    8,1    21869 132132 /var/log/Xorg.0.log
Xorg      927 root    2w   REG    8,1    16469 131327 /var/log/gdm/:0.log

Test result: ramlog cannot be started or stopped at the moment.

I have no idea how to proceed from here.  It seems to me that I have two options:
a) Move all those services to start after ramlog starts
b) Make ramlog start even earlier than it does now (before those services)

Thanks again for any help!

---

