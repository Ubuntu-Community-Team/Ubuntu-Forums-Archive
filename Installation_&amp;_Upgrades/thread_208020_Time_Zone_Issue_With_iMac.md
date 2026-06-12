---
title: "Time Zone Issue With iMac"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by RHTopics on 2006-07-02
I am finding a mixed time environment with my new installation of Dapper.

When I do a date command I get this:

Sun Jul  2 20:22:49 CDT 2006

When I "touch" a test file to set its date, I get this:

ted@dapper:~/tmp$ touch test
ted@dapper:~/tmp$ ls -l test
-rw-r--r-- 1 ted ted 0 2006-07-03 02:24 test

I would like to set the system to use local time instead of UTC, but changing
/etc/default/rcS to make this happen does not seem to work.

From /etc/default/rcS:
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
#

Any suggestions on how to get an iMac to use local time with Dapper.

---

### Post by RHTopics on 2006-07-02
Well, through experimentation, I found out that if you are not connected to the
internet when you boot up the computer, that is when you have the problem with mixed times.

I guess when Ubuntu contacts the ntp server upon booting up, it sets the right time throughout the system.

I also found by going into "Time and Date" from the Administration submenu and then changing the time zone location within the same time zone, that will also correct the problem.

I guess it is a new feature for Dapper :?

---

