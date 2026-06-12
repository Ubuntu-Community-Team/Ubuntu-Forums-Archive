---
title: "pppd terminate right after obtained IP address"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by zhangweiwu on 2012-03-31
Hello. A1200 is my motorola mobile phone with modem capacity. I try to dial up to the Internet by connecting the mobile phone to my Ubuntu 11.10 with a USB cable.

As expected network-manager does not work out of the box. With wvdial, pppd would quit right after having obtained an IP address from the other peer. See log below (just scroll to the bottom of it, I think interesting things happened Mar 31 19:10:34)
```

Mar 31 19:10:26 lugdunnum pppd[1598]: pppd 2.4.5 started by root, uid 0
Mar 31 19:10:26 lugdunnum pppd[1598]: using channel 1
Mar 31 19:10:26 lugdunnum NetworkManager[619]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 31 19:10:26 lugdunnum NetworkManager[619]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar 31 19:10:26 lugdunnum pppd[1598]: Using interface ppp0
Mar 31 19:10:26 lugdunnum pppd[1598]: Connect: ppp0 <--> /dev/ttyACM0
Mar 31 19:10:26 lugdunnum pppd[1598]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9c0d3402>]
Mar 31 19:10:26 lugdunnum pppd[1598]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x9c0d3402>]
Mar 31 19:10:26 lugdunnum pppd[1598]: rcvd [LCP ConfReq id=0x1 <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x54010000> <pcomp> <accomp>]
Mar 31 19:10:26 lugdunnum pppd[1598]: sent [LCP ConfRej id=0x1 <pcomp> <accomp>]
Mar 31 19:10:26 lugdunnum pppd[1598]: rcvd [LCP ConfReq id=0x2 <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x54010000>]
Mar 31 19:10:26 lugdunnum pppd[1598]: sent [LCP ConfAck id=0x2 <mru 1500> <asyncmap 0x0> <auth pap> <magic 0x54010000>]
Mar 31 19:10:26 lugdunnum pppd[1598]: sent [LCP EchoReq id=0x0 magic=0x9c0d3402]
Mar 31 19:10:26 lugdunnum pppd[1598]: sent [PAP AuthReq id=0x1 user="172" password=<hidden>]
Mar 31 19:10:26 lugdunnum pppd[1598]: rcvd [LCP EchoRep id=0x0 magic=0x54010000]
Mar 31 19:10:29 lugdunnum pppd[1598]: rcvd [IPCP ConfReq id=0x2]
Mar 31 19:10:29 lugdunnum pppd[1598]: discarding proto 0x8021 in phase 5
Mar 31 19:10:29 lugdunnum pppd[1598]: sent [PAP AuthReq id=0x2 user="172" password=<hidden>]
Mar 31 19:10:29 lugdunnum pppd[1598]: rcvd [PAP AuthAck id=0x2 "Welcome to Motorola Ezx Software Modem!"]
Mar 31 19:10:29 lugdunnum pppd[1598]: Remote message: Welcome to Motorola Ezx Software Modem!
Mar 31 19:10:29 lugdunnum pppd[1598]: PAP authentication succeeded
Mar 31 19:10:29 lugdunnum pppd[1598]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Mar 31 19:10:29 lugdunnum pppd[1598]: rcvd [IPCP ConfNak id=0x1 <addr 10.187.26.80> <ms-dns1 221.179.38.7> <ms-dns2 120.196.165.7>]
Mar 31 19:10:29 lugdunnum pppd[1598]: sent [IPCP ConfReq id=0x2 <addr 10.187.26.80> <ms-dns1 221.179.38.7> <ms-dns2 120.196.165.7>]
Mar 31 19:10:29 lugdunnum pppd[1598]: rcvd [IPCP ConfAck id=0x2 <addr 10.187.26.80> <ms-dns1 221.179.38.7> <ms-dns2 120.196.165.7>]
Mar 31 19:10:32 lugdunnum pppd[1598]: sent [IPCP ConfReq id=0x2 <addr 10.187.26.80> <ms-dns1 221.179.38.7> <ms-dns2 120.196.165.7>]
Mar 31 19:10:32 lugdunnum pppd[1598]: rcvd [IPCP ConfAck id=0x2 <addr 10.187.26.80> <ms-dns1 221.179.38.7> <ms-dns2 120.196.165.7>]
Mar 31 19:10:34 lugdunnum pppd[1598]: rcvd [IPCP ConfReq id=0x2]
Mar 31 19:10:34 lugdunnum pppd[1598]: sent [IPCP ConfNak id=0x2 <addr 0.0.0.0>]
Mar 31 19:10:34 lugdunnum pppd[1598]: rcvd [LCP TermReq id=0x3 00 00 00 00 00 00]
Mar 31 19:10:34 lugdunnum pppd[1598]: LCP terminated by peer (^@^@^@^@^@^@)
Mar 31 19:10:34 lugdunnum pppd[1598]: sent [LCP TermAck id=0x3]
Mar 31 19:10:34 lugdunnum pppd[1598]: Modem hangup
Mar 31 19:10:34 lugdunnum pppd[1598]: Connection terminated.
Mar 31 19:10:34 lugdunnum avahi-daemon[616]: Withdrawing workstation service for ppp0.
Mar 31 19:10:34 lugdunnum NetworkManager[619]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 31 19:10:34 lugdunnum pppd[1598]: Exit.

```

here is my wvdial.conf and /etc/ppp/peer/wvdial: I do tweeked both a lot, what you see here is the cloest setup to a working one (I think). I verified username/password/APN information are all correct by configuring the mobile phone to dial to the Internet by itself with them. What would you suggest me to do from now?

```

almustafa@lugdunnum:~$ cat /etc/wvdial.conf 
[Dialer Defaults]
Init3 = AT+CGDCONT=1,"IP","cmnet"
Modem = /dev/ttyACM0
Phone = *99***1#
Username = 172
Password = 172
almustafa@lugdunnum:~$ sudo cat /etc/ppp/peers/wvdial
noauth
name wvdial
usepeerdns
novj
novjccomp
maxfail 50
noipdefault
ipcp-accept-local
ipcp-accept-remote
defaultroute
noauth
crtscts
debug
nodeflate
nobsdcomp
-ac
-pc

```

---

### Post by lkraemer on 2012-04-01
[B]
Have you tried setting your pap-secrets and/or chap-secrets file?[/B]

For more information try:
```

man pppd
man pppconfig

```


First, you will need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window (Console):
```

sudo pppconfig

```
You will need your [B]userlogin, password, ISP provider information, and
pap or chap information[/B] for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

The pap-secrets at /etc/ppp/pap-secrets file contains:
(NOTE: File Format for 10.04)
```

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       hostname        ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   hostname        "*"     -
master  hostname        "*"     -
root    hostname        "*"     -
support hostname        "*"     -
stats   hostname        "*"     -

# OUTBOUND connections

# Here you should add your userid password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.
#       *       password
"yourusername@yourisp.net" provider "yourpassword"

```
ASSUME:
your loging name is **GeraldJones**
your password is [B]MyPassWord
[/B]
Your last section of the pap-secrets file should be:
```

# OUTBOUND connections

# Here you should add your userid & password to connect to your providers via
# PAP. The * means that the password is to be used for ANY host you connect
# to. Thus you do not have to worry about the foreign machine name. Just
# replace password with your password.
# If you have different providers with different passwords then you better
# remove the following line.

#	*	password
"**GeraldJones**" provider "**MyPassWord**"

```



Also your wvdial.conf looks a bit suspicious................
In a Terminal window do:
```

sudo wvdialconf /etc/wvdial.conf

```
You should get a configuration file something like this at
/etc/wvdial.conf (you may need to add/modify a few things...)
wvdial.conf contains something like this, but yours will be slightly different:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```
Now assuming that your pap-secrets and or your chap-secrets file is
correct you should be able to use wvdial to dial the connection with:
```

wvdial /etc/wvdial.conf

```

If pppd is dropping the connection it typically means your userid and/or password is incorrect, OR your configuration for pppd is incorrect.

**REF:**
wvdial.conf info:
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf)

PPP HOWTO:
[http://tldp.org/HOWTO/PPP-HOWTO/index.html](http://tldp.org/HOWTO/PPP-HOWTO/index.html)

PAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1034.html](http://tldp.org/HOWTO/PPP-HOWTO/x1034.html)

CHAP-SECRETS info:
[http://tldp.org/HOWTO/PPP-HOWTO/x1053.html](http://tldp.org/HOWTO/PPP-HOWTO/x1053.html)

Setting up PPP Manually
[http://tldp.org/HOWTO/PPP-HOWTO/manual.html](http://tldp.org/HOWTO/PPP-HOWTO/manual.html)


lk

---

### Post by zhangweiwu on 2012-04-01
Thanks a lot for your reply. It is really detailed & serve as a good guide for general audience.

I am curious why you suggested to set up PAP when my first log showed "PAP authentication succeeded". My humble understanding is that the log showed not only PAP is successful, but also IP address is given by peer, and then something happened to have terminated the connection. (Pay attention to what happend Mar 31 19:10:34). So whatevern went wrong is not related to PAP. Besides, I checked with my ISP and confirmed "any username / password would work", because ISP accounts phone number.

But I followed your instruction anyway, and, to my expectation, the ppp error log this time looks the same as my previous error log (with the same "PAP succeeded" message). Do you suggest me to put the new ppp log message here again?

---

### Post by lkraemer on 2012-04-01
I'm merely suggesting things you can look for to try and get the pppd connection functional.

There isn't a need to repeat the error message.

In your /etc/wvdial.conf file, you can try adding the following
one item at a time to see if they help.......
```

Auto DNS = yes
New PPPD = yes
Stupid mode = yes
;carrier check = no
ISDN = 0

```

lk

---

### Post by zhangweiwu on 2012-04-05
Dear lkraemer

I tried all these options one at a time, that counts a total of 5 trials, and the wvdial behavior / pppd log doesn't have noticable change, all failed. Thanks for all the help along the way. when I have more time, I'll see if I can dig deeper to find out what exactly caused the problem.

---

### Post by lkraemer on 2012-04-05
I think these sites will assist you............
[http://www.hohndel.org/communitymatters/ming/motorola-ming-as-gprs-modem-for-the-eeepc/](http://www.hohndel.org/communitymatters/ming/motorola-ming-as-gprs-modem-for-the-eeepc/)
[http://www.motorolafans.com/forums/a1200-general-chat/26533-using-motorola-a1200-as-internet-gateway-using-gprs-on-ubuntu-9-04-8-10-a.html](http://www.motorolafans.com/forums/a1200-general-chat/26533-using-motorola-a1200-as-internet-gateway-using-gprs-on-ubuntu-9-04-8-10-a.html)

**Make sure that the USB mode of the phone is set to USB Modem.**

Be sure to read all the COMMENTS at the bottom of the BLOG.

lk

---

