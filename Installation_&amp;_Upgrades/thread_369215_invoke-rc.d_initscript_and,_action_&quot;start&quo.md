---
title: "invoke-rc.d: initscript and, action &quot;start&quot; failed"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by Niels L Ellegaard on 2007-02-24
Dear great masters

I just used sudo update-manager -c to upgrade my laptop, but somehow things went wrong and I cannot use apt-get anymore. The problem seems to be related to restarting the 
Auto Nice Daemon, I would be grateful for some advice on how to proceed from here.

Should I file a bug report?

                   Thanks in advance

                                     Niels

PS: I hope to be forgiven for the following spam :

root@niels:~# /etc/init.d/and start

root@niels:~# /usr/sbin/invoke-rc.d and start

Starting auto nice daemon: invoke-rc.d: initscript and, action "start" failed.
root@niels:~# apt-get remove gfortran
Reading package lists... Done
Building dependency tree... Done
Package gfortran is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up and (1.2.2-1.1) ...
Starting auto nice daemon: invoke-rc.d: initscript and, action "start" failed.
dpkg: error processing and (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 and
E: Sub-process /usr/bin/dpkg returned an error code (1)

root@niels:~# sh -x  /usr/sbin/invoke-rc.d and start
+ RUNLEVEL=/sbin/runlevel
+ POLICYHELPER=/usr/sbin/policy-rc.d
+ INITDPREFIX=/etc/init.d/
+ RCDPREFIX=/etc/rc
+ BEQUIET=
+ MODE=
+ ACTION=
+ FALLBACK=
+ NOFALLBACK=
+ FORCE=
+ RETRY=
+ RETURNFAILURE=
+ RC=
+ set +e
+ test 2 -eq 0
+ state=I
+ test 2 -gt 0
+ test I != III
+ verifyparameter and
+ test 1 -eq 0
+ test 1 -ne 1
+ return
+ INITSCRIPTID=and
+ state=II
+ shift
+ test 1 -gt 0
+ test II != III
+ verifyparameter start
+ test 1 -eq 0
+ test 1 -ne 1
+ return
+ ACTION=start
+ state=III
+ shift
+ test 0 -gt 0
+ test III != III
+ test ! -f /etc/init.d/and
+ /sbin/runlevel
+ sed s/.*\ //
+ RL=2
+ test ! 0
+ test x2 = x0
+ test x2 = x6
+ test x2 != x
+ ls -d -Q /etc/rc2.d/S20and
+ xargs
+ SLINK=/etc/rc2.d/S20and
+ ls -d -Q /etc/rc2.d/K[0-9][0-9]and
+ xargs
+ KLINK=
+ ls -d -Q /etc/rcS.d/S[0-9][0-9]and
+ xargs
+ SSLINK=
+ verifyrclink /etc/rc2.d/S20and
+ doexit=
+ test 1 -gt 0
+ test ! -L /etc/rc2.d/S20and
+ test ! -f /etc/rc2.d/S20and
+ shift
+ test 0 -gt 0
+ test x != x
+ return 0
+ RC=
+ testexec /etc/rc2.d/S20and
+ test 1 -gt 0
+ test -x /etc/rc2.d/S20and
+ return 0
+ RC=104
+ testexec /etc/init.d/and
+ test 1 -gt 0
+ test -x /etc/init.d/and
+ return 0
+ test x104 = x
+ querypolicy
+ policyaction=start
+ test x104 = x101
+ test x/usr/sbin/policy-rc.d != x
+ test -x /usr/sbin/policy-rc.d
+ test x104 = x
+ return
+ test x = xquery
+ test x != x
+ test 104 -eq 104
+ testexec /etc/init.d/and
+ test 1 -gt 0
+ test -x /etc/init.d/and
+ return 0
+ RC=102
+ setechoactions start
+ test 1 -gt 1
+ echoaction=
+ test ! -z start
+ getnextaction start
+ saction=start
+ shift
+ ACTION=
+ test ! -z
+ /etc/init.d/and start
Starting auto nice daemon: + RC=1
+ test ! -z 
+ test ! -z 
+ printerror initscript and, action "start" failed.
+ test x = x
+ basename /usr/sbin/invoke-rc.d
+ echo invoke-rc.d: initscript and, action "start" failed.
invoke-rc.d: initscript and, action "start" failed.
+ exit 1

root@niels:~# dpkg -l and initscripts
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name             Version          Description
+++-================-================-================================================
iF  and              1.2.2-1.1        Auto Nice Daemon
ii  initscripts      2.86.ds1-14.1ubu Scripts for initializing and shutting down the s

---

### Post by Niels L Ellegaard on 2007-02-24
I solved the problem myself

sudo apt-get remove and

Sorry about the noise.

---

### Post by mobrien118 on 2008-02-24
No worries on the noise.

You just helped me solve this "should have been obvious" promlem I was having with a completely different package.

Thanks!!!

---

