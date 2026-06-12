---
title: "Ubunto 5.10 Breezy (AMD64)...any modems is seen !!! Help me"
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by Cocomi on 2005-09-29
I am trying to install a ADSL modem (before adsl usb and after I have failed :confused:  I have tried a modem router ethernet...the result? this is not even seen on UBUNTU 5.10 :rolleyes: )
.....any modems is seen. 
I point out the tests of the
two types of modem under. I pray you if someone also has an alone idea
of the why this happens tells me it, this problem  holds me occupied
by days and any technician  knows how to resolve the problem


1) I have tried (Precise that have performed a lot of tests and always
following the procedures that I have found in internet and that
someone has pointed out me in the forums but nobody has ever resolved
the problem. ) to install the modem Digicom Michelangelo USB CX using
the drivers eciadsl and following footstep to footstep the
instructions ( Precise that this modem is expressly supported by the
driver eciadsl ) . At the end I try to connect but the modem  is not
recognized. The error message is the following:

root@systemrob:~# ./eciadsl-doctor 

You are using linux kernel version 2.6.12-8-amd64-generic
Support for USB is OK
Preliminary USB device filesystem is OK
dabusb module is not loaded: OK
UHCI support is OK
OHCI support is not needed
/dev/ppp is OK
HDLC support is OK
HDLC support is OK (no bug)
I cannot find your ADSL modem: Fatal:???: 
root@systemrob:~#


2) To this point considering that nobody knew me to point out whether
to do for resolving the problem and considering that the modem
ethernet is easier to be shaped I have tried with this type of modem
(Sitecom DC213). I have connected the modem and then I have used
pppoeconf to shape. Everything ok actually to that I try to connect
me, here what the message is:

root@systemrob:~# pppoe-start
................TIMED OUT
/usr/sbin/pppoe-start: line 191: 17478 Terminated   $CONNECT "$@" >/d
ev/null 2>&1  :???: 



I have made some controls if there is some magician that succeeds them
in interpreting. I bring here them under

root@systemrob:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:8D:98:9A :razz: 
          inet addr:192.168.1.105  Bcast:255.255.255.255
Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe8d:989a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14232 (13.8 KiB)  TX bytes:3525 (3.4 KiB)
          Interrupt:23 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:25436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7631080 (7.2 MiB)  TX bytes:7631080 (7.2 MiB)




root@systemrob:~# pppoe-status
pppoe-status: Link is down (can't read pppoe PID file
/var/run/pppoe.conf-pppoe.pid.pppoe)    :confused: 
root@systemrob:~#


Thanks

Cristian

---

