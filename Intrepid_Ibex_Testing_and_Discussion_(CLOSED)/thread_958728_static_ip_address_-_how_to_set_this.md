---
title: "static ip address - how to set this?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jynyl on 2008-10-25
Running Kubuntu 8.10 rc1
In System Settings > Network Settings, there seems to be no fields to set a static IP address.

Alternatively, right click on the network icon in the panel gives an empty box, but the only option is to add connections.  I don't want to add a connection, just edit the current one to a static IP address.

TIA

Peter

---

### Post by jynyl on 2008-10-26
Perhaps there isn't a way to set this, it is a bug in Intrepid.
[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/280762]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/280762")

---

### Post by cbr_king on 2008-10-26
[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=629280](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=629280)

Download **wicd_1.5.3_all.deb**, uninstall Network Manager, install wicd. Customize your settings...

It works for me like a charm :rolleyes:

---

### Post by jynyl on 2008-10-26
thanks
Adept couldn't find Network Manager to remove it, so I used Synaptic.

---

### Post by Dedoimedo on 2008-10-26
Hello,

The functionality is there, just look more carefully:

[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html)

Check under "More about network manager ..."

Cheers,
Dedoimedo

---

### Post by jynyl on 2008-10-26
> **Dedoimedo said:**
> 
The functionality is there, just look more carefully:
[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html)
Check under "More about network manager ..."

The example on that page looks like Ubuntu.  In Kubuntu, the Network Manager box that comes up is quite different, and in it I couldn't find any existing wired connections to edit.

---

### Post by Dedoimedo on 2008-10-26
What's the output of ifconfig -a on your machine?
Dedoimedo

---

### Post by jynyl on 2008-10-26
This is with Network Manager removed and wicd installed.
```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:86:4d:5f
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe86:4d5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3800807 (3.8 MB)  TX bytes:623057 (623.0 KB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4672 (4.6 KB)  TX bytes:4672 (4.6 KB)

pan0      Link encap:Ethernet  HWaddr 2a:38:3d:e3:be:3c
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Dedoimedo on 2008-10-27
I thought you were still using the NM ... nevermind.
Dedoimedo

---

### Post by jongkind on 2008-10-27
> **Dedoimedo said:**
> Hello,

The functionality is there, just look more carefully:

[http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html)

Check under "More about network manager ..."

Cheers,
Dedoimedo

Dedoimedo,

I'm aware of this functionality. The problem is that after rebooting the machine forgets the settings of a static IP address.

---

### Post by Dedoimedo on 2008-10-28
Hello,
That's strange. I have not noticed this.
I'll be testing some more ...
Dedoimedo

---

### Post by natros on 2008-10-28
> **jongkind said:**
> Dedoimedo,

I'm aware of this functionality. The problem is that after rebooting the machine forgets the settings of a static IP address.

I have the same problem :(

---

### Post by misterhead on 2008-10-28
I have been screwing with this new network manager for a while now, since it came stock with Fedora 9, and I absolutely love it. I have many different static IP setups stored for configuring various pieces of hardware for work, and if you check the box for "connect automatically, it will, as long as you are not being served DHCP. For me that got rid of the headache of expecting dhcp to work instantly after forgetting that I set myself up "static" to troubleshoot some flow monitoring RTU earlier that day.Not to mention, the ability to have a different static connection for the default state of every type of device that I touch as well as different static connections for the individual networks they are getting put on, once they are configured, and the ability to switch between them instantly with 2 mouse clicks, is a Godsend.
I think that this network manager is a brilliant step in the right direction, and at the risk of sounding like a jerk, which I am in NO WAY trying to do, I'm just curious... What scenarios are the op and some posters in, where they need a static IP, but don't want to create one, and DHCP is present.

---

### Post by natros on 2008-10-28
I don't understand why is ubuntu releasing an unstable version (svn20081018t105859). The last stable version available is 0.6.5 ( [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/](http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/))

---

