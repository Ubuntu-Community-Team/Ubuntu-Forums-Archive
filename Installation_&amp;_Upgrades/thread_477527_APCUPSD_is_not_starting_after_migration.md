---
title: "APCUPSD is not starting after migration"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by theQmaster on 2007-06-18
Hi,

I migrated from 5.04 to 6.10 and all looks just fine besides the fact that the apcupsd is not starting...

[B]mc@gsi:/var/run$ sudo /etc/init.d/apcupsd force-reload
Restarting APC UPS power management: Stopping APC UPS power management: apcupsd.
No process in pidfile `/var/run/apcupsd.pid' found running; none killed.

Starting APC UPS power management:
A copy of the daemon is still running.  If you just stopped it,
please wait about 5 seconds for it to shut down.
[/B]

Well I know what you where thinking... there is another process running, no it ain't!
There is no pid file under /var/lock nor under /var/run - trying to check the status of the server returns
[B]
FATAL ERROR in apcaccess.c at line 252
tcp_open: cannot connect to server 127.0.0.1 on port 3551.
ERR=Connection refused
[/B]


Now I've tried to list the devices
[B]
cat /proc/bus/usb/devices

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=051d ProdID=0002 Rev= 1.06
S:  Manufacturer=American Power Conversion
S:  Product=Back-UPS BR  800 FW:9.o2 .D USB FW:o2
S:  SerialNumber=QB0603297416
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 24mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms
[/B]

Also I see the **/dev/hiddev0**

My **apcups.conf** looks like this ( the most important entries)
[B]
UPSCABLE usb
UPSTYPE usb
DEVICE
LOCKFILE /var/lock
UPSCLASS standalone
UPSMODE disable
[/B]
NETSERVER on
NISIP 127.0.0.1
NISPORT 3551


What in the world it's happening. I tried to use the conf file that was working in 5.06 and it didn't work!

Under my events I see that the server exist right away and there is no additional info. How can I add debug info ?
**Mon Jun 18 10:33:13 CDT 2007  apcupsd exiting, signal 15**


Thanks a lot for looking!
MC

---

### Post by theQmaster on 2007-06-18
Any idea ?

> **theQmaster said:**
> Hi,

I migrated from 5.04 to 6.10 and all looks just fine besides the fact that the apcupsd is not starting...

[B]mc@gsi:/var/run$ sudo /etc/init.d/apcupsd force-reload
Restarting APC UPS power management: Stopping APC UPS power management: apcupsd.
No process in pidfile `/var/run/apcupsd.pid' found running; none killed.

Starting APC UPS power management:
A copy of the daemon is still running.  If you just stopped it,
please wait about 5 seconds for it to shut down.
[/B]

Well I know what you where thinking... there is another process running, no it ain't!
There is no pid file under /var/lock nor under /var/run - trying to check the status of the server returns
[B]
FATAL ERROR in apcaccess.c at line 252
tcp_open: cannot connect to server 127.0.0.1 on port 3551.
ERR=Connection refused
[/B]


Now I've tried to list the devices
[B]
cat /proc/bus/usb/devices

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=051d ProdID=0002 Rev= 1.06
S:  Manufacturer=American Power Conversion
S:  Product=Back-UPS BR  800 FW:9.o2 .D USB FW:o2
S:  SerialNumber=QB0603297416
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 24mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   6 Ivl=10ms
[/B]

Also I see the **/dev/hiddev0**

My **apcups.conf** looks like this ( the most important entries)
[B]
UPSCABLE usb
UPSTYPE usb
DEVICE
LOCKFILE /var/lock
UPSCLASS standalone
UPSMODE disable
[/B]
NETSERVER on
NISIP 127.0.0.1
NISPORT 3551


What in the world it's happening. I tried to use the conf file that was working in 5.06 and it didn't work!

Under my events I see that the server exist right away and there is no additional info. How can I add debug info ?
**Mon Jun 18 10:33:13 CDT 2007  apcupsd exiting, signal 15**


Thanks a lot for looking!
MC

---

### Post by yabbadabbadont on 2007-06-18
What is the error message when you just try to do a normal start?

sudo /etc/init.d/apcupsd start

---

### Post by theQmaster on 2007-06-18
[B]mc@gsi:~$ sudo /etc/init.d/apcupsd start
Starting APC UPS power management:
A copy of the daemon is still running.  If you just stopped it,
please wait about 5 seconds for it to shut down.
[/B]

[COLOR="Red"]But there is nothing running at port 3551![/COLOR]

I will try to reinstall it and see if that makes any difference.


> **yabbadabbadont said:**
> What is the error message when you just try to do a normal start?

sudo /etc/init.d/apcupsd start

---

### Post by yabbadabbadont on 2007-06-18
That just means that there was a process called apcupsd running somewhere.  Try running "sudo killall -9 apcupsd" and then try starting it again.

---

### Post by theQmaster on 2007-06-18
:KS:KS:KS:KS:KS

That did it but it's interesting the port wasn't open and I didn't find any pid file under /var/run...

Thanks a lot ! Very much appreciate it!!!!
Q


> **yabbadabbadont said:**
> That just means that there was a process called apcupsd running somewhere.  Try running "sudo killall -9 apcupsd" and then try starting it again.

---

### Post by yabbadabbadont on 2007-06-18
It was probably a zombie process.  i.e. it was still running, but wasn't responding to any input.

---

### Post by BlueN1nja on 2007-07-10
EDIT: Solved-needed to set the lockfile directory back to what it was in apcupsd.conf; I had set it to /var/lock/apcupsd which caused problems due to not existing.

I'm getting a very similar problem on 7.04.

```

blueninja@callisto:/etc/apcupsd$ sudo /etc/init.d/apcupsd start
Starting APC UPS power management: apcupsd.
blueninja@callisto:/etc/apcupsd$ ps aux|grep apc
blueninja    5875  0.0  0.2   2880   744 pts/2    R+   17:59   0:00 grep apc
blueninja@callisto:/etc/apcupsd$ sudo /etc/init.d/apcupsd restart
Restarting APC UPS power management: Stopping APC UPS power management: apcupsd.
start-stop-daemon: warning: failed to kill 5869: No such process
1 pids were not killed
No process in pidfile `/var/run/apcupsd.pid' found running; none killed.

Starting APC UPS power management: apcupsd.
blueninja@callisto:/etc/apcupsd$ apcaccess status
FATAL ERROR in apcaccess.c at line 252
tcp_open: cannot connect to server 127.0.0.1 on port 50142.
ERR=Connection refused
```

Port 50412 is a port I arbitrarily chose when I was getting an error on the default (3551?). Netserver is turned off in apcupsd.conf.

How can I fix this?

---

