---
title: "Gnome-ppp doesn't maintain myconnection"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by eAi-T0ky0 on 2008-10-17
[CENTER]hi all
  I have some problems with my USB Huawei e220 My problem isI´ve configured several times /etc/wvdial.conf I almost get modem connected but I always get an error in idle time that doesn´t let me contiune.

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","pps";
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Oct 18 00:25:18 2008
--> Pid of pppd: 6215
--> Disconnecting at Sat Oct 18 00:25:19 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)
```

  I´ll really appreciate if you can guide me, last time with Debian in my PC I got my modem ready, but now I can´t.[/CENTER]

---

### Post by eAi-T0ky0 on 2008-10-17
Help!!!

---

### Post by Waugh on 2008-10-22
Having almost the same issue here, except mine will disconnect every 2.5 minutes on the dot.

---

### Post by robert shearer on 2008-10-22
It has been a while since I had to use dial-up but I recall that the fix was to include a 'pause' to allow the I.D and password to complete before starting ppp.
From your post it seems that ppp is started right away and no "handshake" is happening.(unless you have edited those from your post?)

> --> Carrier detected.  Starting PPP immediately.

Also have you tried the man pages as the output suggests?

> --> man pppd explains pppd error codes in more detail

Here is the section...  

   2      An error was detected in processing the options given,  such  as
              two mutually exclusive options being used.


and a link....
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

---

