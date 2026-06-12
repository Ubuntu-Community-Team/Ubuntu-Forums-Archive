---
title: "Why APC UPS tries to attach via serial port?"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-16
Hi all, 
 I'm having issues with an APC UPS-BR 800 which I bought couple of months ago. 

I'm not able to get apcupsd to start. 

```

/etc/init.d/apcupsd start
Starting UPS power management: Terminating due to configuration file errors.


```as well as 

```

/etc/init.d/apcupsd status
Error contacting apcupsd @ localhost:3551: Connection refused
```This is the issue I see as from /var/log/messages :-

```

cat /var/log/apcupsd.events
Wed Oct 15 13:42:58 IST 2008  apcupsd FATAL ERROR in smartsetup.c at line 171
PANIC! Cannot communicate with UPS via serial port.
Please make sure the port specified on the DEVICE directive is correct,
and that your cable specification on the UPSCABLE directive is correct.
Wed Oct 15 13:42:58 IST 2008  apcupsd error shutdown completed
Wed Oct 15 15:30:46 IST 2008  apcupsd FATAL ERROR in smartsetup.c at line 171
PANIC! Cannot communicate with UPS via serial port.
Please make sure the port specified on the DEVICE directive is correct,
and that your cable specification on the UPSCABLE directive is correct.
Wed Oct 15 15:30:46 IST 2008  apcupsd error shutdown completed
```Would be attaching my apcupsd.conf in case you guys see some issue. Also filed a bug at [lpbug]284180[/lpbug]


Looking forward for comments and suggestions to the same.

---

### Post by mrsteveman1 on 2008-10-16
Is yours USB? you have to change the config file to use USB if thats the case (its commented where you need to change it).

---

### Post by ShirishAg75 on 2008-10-16
mrsteveman1 I have it commented out, where else or which other config file does it need to be commented out?

I know only /etc/apcupsd/apcupsd.conf and the relevant usb lines I am giving below which are there in this config file . 

```

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE usb

# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
UPSTYPE usb
DEVICE  

```

The cable I have got is a cable which has usb connectivity at one end (Computer) and RJ-45 connector which connector (in the UPS) as shown at 

[http://www.apcupsd.org/manual/Cables.html#SECTION0003181100000000000000](http://www.apcupsd.org/manual/Cables.html#SECTION0003181100000000000000)

---

