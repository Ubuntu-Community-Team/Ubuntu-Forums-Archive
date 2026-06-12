---
title: "Safaricom modem on Ubuntu remix"
date: 2009-08-29
forum: Kenyan Team - Kenya
---

### Post by vtired on 2009-08-29
Dear Kenyan Ubuntists,
I have problems with Safaricom modem on Ubuntu netbook remix. The connection wizard satrts very well and even has an option for kenya, safaricom. The first connection worked fine but when I tried a second time, the nm asked for a password, instead of pin. Anyone there with an idea of how to get a stable connection?
The safaricom guys aren't familair with Ubuntu.

---

### Post by fuzzyk.k on 2009-10-08
it normally asks for a password when the network is jammed , try around midnight

---

### Post by rwaki on 2009-11-03
> **vtired said:**
> Dear Kenyan Ubuntists,
I have problems with Safaricom modem on Ubuntu netbook remix. The connection wizard satrts very well and even has an option for kenya, safaricom. The first connection worked fine but when I tried a second time, the nm asked for a password, instead of pin. Anyone there with an idea of how to get a stable connection?
The safaricom guys aren't familair with Ubuntu.



Try disabling the PIN using a mobile phone. It worked for me

---

### Post by madcowchow on 2010-07-22
try wvdial instead[INDENT]sudo apt-get install wvdial
[LEFT]sudo nano /etc/wvdial.conf

[/LEFT]
[/INDENT]enter the following:[INDENT][Dialer Defaults]
Phone = *99#
Username = saf
Password = data
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 3600000
Init2 = ATZ
Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Init4 = AT+CGDCONT=1,"IP","SAFARICOM"
[/INDENT]save and:[INDENT]sudo wvdial
[/INDENT]

---

### Post by Akukudanger on 2010-11-22
Hi guys.

I am a newbie in ubuntu. Recently installed ubuntu 10.04 on my laptop. I need to use my safaricom modem to connect to the Internet but so far I have hit a brick wall](*,)](*,)](*,).
After reading several forums on the net about wvdial i got the modem assigned a local ip address  plus the corresponding  primary & secondary DNS addresses. (see output below)

WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","safaricom"
AT+CGDCONT=1,"IP","safaricom"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Nov 23 05:16:35 2010
--> Pid of pppd: 2079
--> Using interface ppp0
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> local  IP address 197.176.51.162
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> remote IP address 10.64.64.64
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> primary   DNS address 196.201.208.2
--> pppd: pj0 &#65533;i0 &#65533;i0 
--> secondary DNS address 209.244.0.3

the problem is that I just **cannot** be able to connect to the internet. I have added the primary & secondary addresses manually to /etc/resolv.conf file but still I **CANNOT** connect to the net.
HELP PLEASE!!!

---

### Post by SecretCode on 2010-11-23
Can you ping the DNS addresses that you get via wvdial?

One of the problems with 3G (anywhere, it seems) is that sometimes you appear to connect but nothing gets through. Sometimes all you can do is wait until the network is less busy.

I'm not in Kenya atm but recently was there and had no problems linking to Safaricom from a 9.10 installation (just using NetworkManager) - but the SIM card was in my phone. I assume you are using the dongle supplied by Safaricom?

---

### Post by Akukudanger on 2010-11-23
I guess I finally figured out what my problem is though I still dont have a solution for it.
I normally use my laptop to connect to the office LAN. when I ping the DNS addresses the ping echo seems to go through my ethernet's static IP address. Hence the ping reply brings a" 172.x.x.x icmp_seq=1 Destination Host Unreachable" reply. (the DNS ping is done having unplugged the office LAN)
I guess the OS still considers my Eth0 connection as my 'gateway' even when LAN cable is unplugged and the modem connected.
Any ideas to go around this??

---

### Post by SecretCode on 2010-11-24
Ah - this sounds like a problem I've seen when using a 3G dongle while still on a local network. I get around it by disabling wifi, but if you have a wired connection I don't know if you can disable it. 
 
Post the output of
```
route -n
```
when connected to 3G.

Try the following 2 commands
```
sudo route del default
sudo route add default gw 10.64.64.64
```

---

### Post by Akukudanger on 2010-11-27
sorry for not replying in time. been under with some throat infection...nothing ubuntu related :-)
anyway here,s my route -n output.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.31.41.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.31.41.254   0.0.0.0         UG    100    0        0 eth0

---

### Post by SecretCode on 2010-11-28
Yes, so all your traffic is sent via eth0. Try the route del / route add commands.

---

### Post by Akukudanger on 2010-11-29
Ran the sudo add/ del commands but still I cannot connect to the net. GRRRR!!!!
Anymore ideas up your sleeve?
p.s.Thanks so far for going out of your way to help me out.

---

### Post by SecretCode on 2010-11-29
What does _route -n_ say after you've run those commands?

Maybe Safaricom are just being bad ... 

Try disconnecting and reconnecting up to 10 times - seriously, I've sometimes had to do that in SA and then it works (Windows as well as Linux)

---

### Post by Akukudanger on 2010-12-01
Hey 
I finally hacked it!! :D
ran the  ***sudo route del default*** &  ***sudo route add default gw 10.64.64.64*** commands.
then an idea hit me!! if the system sees my eth0 as my "internet gateway" what if I disabled the interface??
ran the command ***sudo ifconfig eth0 down*** and put the eth0 in an inactive state.
I am replying this post on my HSDPA connection.
thanks alot Secretcode!!!

---

### Post by SecretCode on 2010-12-03
> **Akukudanger said:**
> put the eth0 in an inactive state.

That's gotta help! Happy surfing!

---

### Post by edug on 2010-12-25
alternatively you can just shut down that interface!
when working as root;
root@edu-threat~#ifconfig eth0 down
*this will shut the interface down*
then manually add a route to your rooting table!

do not know if It helped you or not!

*cheers*


> **Akukudanger said:**
> sorry for not replying in time. been under with some throat infection...nothing ubuntu related :-)
anyway here,s my route -n output.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
172.31.41.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.31.41.254   0.0.0.0         UG    100    0        0 eth0

---

### Post by gemeinschaft on 2011-07-04
I have edited the wvdial.conf to refelct the settings for Safaricom. 

What I am trying to do is script opening the application and initiating a connection on the desktop. 

I am still working on learning how to write scripts, so I was wondering, has anyone already written a script that initiates a connection to Safaricom? 

I am trying to get this so that the user (in this case, a 60 year old woman) can just click and connect. 

Thanks in advance.

---

### Post by dannydynx on 2011-11-15
Hi,

I would like introduce DNS Solutions To you all. 

We offer:-
[LIST]
[*]Home, Office, Business & Cyber Café Networking
[*]Technical Support, Repairs & Data Recovery
[*]Internet Installation and Configuration
[*]Cyber Café Ubuntu Installation & Timer Config.
[*]Gateway & Firewall Inst & Configuration (to block Porn and other unwanted internet acces in cyber cafe's, office and home internet)
[*]ICT Consultants
[/LIST]


Contact us on:

**[COLOR="Blue"]0733 366808[/COLOR]** or Email **_[COLOR="Blue"]dnssolutionskenya@gmail.com[/COLOR]_**

Thank you all!!!!

---

