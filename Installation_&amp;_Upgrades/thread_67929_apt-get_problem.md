---
title: "apt-get problem"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by ericsp on 2005-09-21
When I try to do an apt-get upgrade, I get the following error:

The following packages will be REMOVED:
  libsqliteodbc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 545kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 80247 files and directories currently installed.)
Removing libsqliteodbc ...
/var/lib/dpkg/info/libsqliteodbc.postrm: line 27: db_stop: command not found
dpkg: error processing libsqliteodbc (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 libsqliteodbc
E: Sub-process /usr/bin/dpkg returned an error code (1)

-------

Please help!
<Thanks>
Eric :???:  :???:

---

### Post by banadushi on 2005-09-21
Try running
```

# dpkg --configure -a

```

and then
```

# apt-get remove libsqliteodbc

```

Let me know if it still borks out.  It sounds like the is pending configure stuff needing to happen.

Have fun!

Jason

---

### Post by ericsp on 2005-09-22
Thanks for the help, Jason. Unfortunately it did not work:

root@Tantalos:/home/ericsp # dpkg --configure -a
root@Tantalos:/home/ericsp # apt-get remove libsqliteodbc
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libsqliteodbc
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 545kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 80247 files and directories currently installed.)
Removing libsqliteodbc ...
/var/lib/dpkg/info/libsqliteodbc.postrm: line 27: db_stop: command not found
dpkg: error processing libsqliteodbc (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 libsqliteodbc
E: Sub-process /usr/bin/dpkg returned an error code (1)


-----

other duggestions?

Eric

---

