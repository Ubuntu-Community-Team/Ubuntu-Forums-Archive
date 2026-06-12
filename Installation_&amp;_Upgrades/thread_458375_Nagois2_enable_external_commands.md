---
title: "Nagois2 enable external commands"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by gmcf on 2007-05-29
Hello,
I have just upgraded to nagios2 from nagios 1 on 7.04.
I want to acknowledge events and add comments from my browser
and by default external commands are disabled.

in nagios.cfg I have set the following.
check_external_commands=1
log_external_commands=1

in my browser I get....
<browser>
Error: Could not stat() command file '/var/lib/nagios2/rw/nagios.cmd'!

The external command file may be missing, Nagios may not be running, and/or Nagios may not be checking external commands.

An error occurred while attempting to commit your command for processing.

</browser>

Here is an ls from /var/lib/nagios2
drwx------ 2 nagios www-data    23 2007-05-29 20:52 rw
and from rw
prw-rw---- 1 nagios nagios 0 2007-05-29 20:52 nagios.cmd

Everything else is at default settings from the install of nagios2 

Any suggestions ?

Other than this Nagios is running fine, checking about 10 service and generating events.

---

### Post by gmcf on 2007-05-30
Oops.

All it needed was
/etc/nagios2#/etc/init.d/nagios2 stop
Stopping nagios2 monitoring daemon: nagios2.
/etc/nagios2# dpkg-statoverride --update --add nagios www-data 2710 /var/lib/nagios2/rw
/etc/nagios2# dpkg-statoverride --update --add nagios nagios 751 /var/lib/nagios2
/etc/nagios2# /etc/init.d/nagios2 start
Starting nagios2 monitoring daemon: nagios2.

---

