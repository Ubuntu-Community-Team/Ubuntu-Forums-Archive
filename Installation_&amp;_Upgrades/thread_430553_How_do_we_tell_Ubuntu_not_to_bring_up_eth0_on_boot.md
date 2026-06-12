---
title: "How do we tell Ubuntu not to bring up eth0 on boot?"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2007-05-02
Dear Ubuntufolk:

I am using a pcmcia modem and not the eth0 network connection.  However the network connection is being brought up automatically on boot, along with the eth1 connection, which is part of the pcmcia card.  I have to execute 'ifconfig eth0 down' and 'ifconfig eth1 down' before running KPPP.  How do I tell the O/S not to bring the network connections up on boot?  I have tried using System > Administration > Network by unclicking the two network connections and clicking the modem, together with making the modem connection the default connection to the internet, but nothing works.

Thanks.

Whatawonderfulday

---

### Post by mojoman on 2007-05-06
> **Whatawonderfulday said:**
> Dear Ubuntufolk:

I am using a pcmcia modem and not the eth0 network connection.  However the network connection is being brought up automatically on boot, along with the eth1 connection, which is part of the pcmcia card.  I have to execute 'ifconfig eth0 down' and 'ifconfig eth1 down' before running KPPP.  How do I tell the O/S not to bring the network connections up on boot?  I have tried using System > Administration > Network by unclicking the two network connections and clicking the modem, together with making the modem connection the default connection to the internet, but nothing works.

Thanks.

Whatawonderfulday

Have a look at the file /etc/network/interfaces (open it with an editor gedit, kate or mousepad, depending on your ubuntu flavour)
```

sudo gedit /etc/network/interfaces
```

In it, there should be a line like so:
```

auto eth0
```

Try commenting that line out by adding a hash mark, like so

```
# auto eth0
```

This will prevent the system from reading that line (very handy if you later need to undo your changes). Rebbot and see what happens, my guess is that your eth0 will be down untill you bring it up with ipconfig.

/mojoman

---

### Post by Whatawonderfulday on 2007-05-06
To Mojoman:

Thanks, Mr Mojoman, but it didn't work.  After I commented out all the likely lines, /etc/network/interfaces looks like this (numeric '9's due to me)::

auto lo
iface lo inet loopback


# iface eth0 inet dhcp
# address 99.99.99.99
# netmask 999.999.999.999
# gateway 99.99.99.99


# iface eth1 inet dhcp

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp


iface ppp0 inet ppp
provider ppp0

Note that I did all the commenting.  Note also that 'auto ath0' is what I found.  A typo?  When I want to use the network again, should I change it to 'auto eth0'?  Note that eth1 is the network part of the pcmcia combined LAN and 56K modem.  I don't know what 'wlan0' would refer to.  'l0' is the local loopback.

ifconfig shows on reboot after the commenting:

root@whatawonderfulday:/home/tomsmithuser# ifconfig

eth0      Link encap:Ethernet  HWaddr 99:99:99:99:99:99  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:10 Base address:0x4000 



eth1      Link encap:Ethernet  HWaddr 99:99:99:99:99:99  

          inet6 addr: ABCD::999:ABCD:ABCD:ABCD/99 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:6 errors:0 dropped:0 overruns:0 carrier:6

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)

          Interrupt:3 Base address:0x300 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:72 errors:0 dropped:0 overruns:0 frame:0

          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:5384 (5.2 KiB)  TX bytes:5384 (5.2 KiB)



root@whatawonderfulday:/home/tomsmithuser# ifconfig eth0 down

root@whatawonderfulday:/home/tomsmithuser# ifconfig eth1 down

root@whatawonderfulday:/home/tomsmithuser# ifconfig

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:80 errors:0 dropped:0 overruns:0 frame:0

          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:5864 (5.7 KiB)  TX bytes:5864 (5.7 KiB)

After bringing up kppp using the pcmcia modem:



root@whatawonderfulday:/home/tomsmithuser# ifconfig

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:80 errors:0 dropped:0 overruns:0 frame:0

          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:5864 (5.7 KiB)  TX bytes:5864 (5.7 KiB)



ppp0      Link encap:Point-to-Point Protocol  

          inet addr:99.99.99.9  P-t-P:99.99.99.99  Mask:255.255.255.255

          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1

          RX packets:6 errors:1 dropped:0 overruns:0 frame:0

          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:3 

          RX bytes:122 (122.0 b)  TX bytes:61 (61.0 b)

If you have any ideas, I would appreciate hearing them.

Whatawonderfulday

---

