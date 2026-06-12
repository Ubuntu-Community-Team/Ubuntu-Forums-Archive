---
title: "Problem configuring idea net setter in ubuntu 9.10"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2010-09-09
Hi,

I am trying to configure my idea net setter on my ubuntu 9.10.

please find the wvdial.conf file

   durga@durga-laptop:~$ cat /etc/wvdial.conf
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB1 
Username = 9342940513 
Password = 9342940513 
CBaud = 460800


[IDEA Net  Setter]

Phone = *99#
Username = 1234567890
Password = 7890
New PPPD = yes
Modem = /dev/ttyUSB0
Baud = 115200
SetVolume = 0
[Modem 0 ]
Dial Command = ATDT
Init = ATZ
init2 = AT + CRM = 1
Flowcontrol = ( CRTSCTS )
Stupid Mod = 1
Inherits = Modem 0


and the output of wvdial is 

durga@durga-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.



Let me know if there is any wrong in my configuration.


Thanks
durga

---

### Post by durga11 on 2010-09-09
Hi,

I followed the below link and edited the wvdial.conf file

[http://technolark.blogspot.com/2009/...tu-jaunty.html]("http://technolark.blogspot.com/2009/05/idea-netsetter-on-ubuntu-jaunty.html")

check the output of sudo wvdial and let me know any thing wrong in my configuration.

 durga@durga-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
NO CARRIER
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Sep  9 14:37:36 2010
--> Pid of pppd: 3445
--> Using interface ppp0
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> local  IP address 27.97.2.104
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;/[08]X&#65533;/[08]`&#65533;/[08]X&#65533;/[08] 

Thanks
Durga

---

### Post by suryak on 2010-12-31
Actually don't make it complicated.. 
Even I use idea netsetter modem and i connected it without doing all this things..
Do this ::
1. Make sure that you connected your modem
2..On the Right Top of the screen in the task bar of ubuntu 9.10, you'll find a network connection option beside volume icon.. 
click on that.
3. Now you'll find that your modem is detected there, if not don't worry, no problem..
click on mobile broadband  option, in that select your network (Airtel, Idea, etc).. 
If its not there type your network name.
Now click forward... and then type your network's APN address
(search in google for your network apn address.. or call your service provider)

4. Its done.. your process is done. .
5. now connect it..
This is what that happened to me.. ( i'm using that now)

---

