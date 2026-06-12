---
title: "NetworkManager0.7 explain me this.."
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-07-29
$ sudo /etc/init.d/networking stop
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0
$ sudo ifconfig eth0
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.27  Bcast:192.168.1.31  Mask:255.255.255.224
          inet6 addr: fe80::250:baff:feb3:9601/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2136 errors:0 dropped:0 overruns:16 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:774844 (756.6 KB)  TX bytes:349873 (341.6 KB)
          Interrupt:11 Base address:0xb400

Where the hell is the "192.168.1.27" ip?

I'm not sure it is NM 0.7, but where does it get that ip?

```

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0


```

---

### Post by DavidONE on 2008-07-29
That IP is assigned to you by your router, I believe.

Your router control panel will be at [http://192.168.0.1](http://192.168.0.1) (for Netgear, usually different for other manufacturers).  From there you can query assigned IPs.

---

### Post by grigio on 2008-07-29
> **DavidONE said:**
> That IP is assigned to you by your router, I believe.

Your router control panel will be at [http://192.168.0.1](http://192.168.0.1) (for Netgear, usually different for other manufacturers).  From there you can query assigned IPs.

I don't have a router, just an ethernet adsl modem

---

### Post by t.alex on 2008-07-29
your answer is in '/var/log/syslog'
take a look there
avahi daemon may be messing with your network. i always shut it down right from the beginning  :)

---

### Post by psyke83 on 2008-07-29
> **grigio said:**
> I don't have a router, just an ethernet adsl modem

On other operating systems or older Ubuntu versions, do you need to specify manual connection settings (IP address, DNS, gateway)? If not, then your modem works as a DHCP server and assigns an IP address automatically.

Otherwise, see this: [http://blogs.gnome.org/dcbw/2008/04/16/anything-less-than-the-best-is-a-felony/](http://blogs.gnome.org/dcbw/2008/04/16/anything-less-than-the-best-is-a-felony/)

---

### Post by grigio on 2008-07-31
I solved removing NW0.7 and upgrading the kernel. Now the IP I set is the ip I get :)

---

### Post by kfazz on 2008-07-31
i think /etc/init.d/networking stop doesn't turn off NM.
sudo /etc/dbus-1/event.d/25NetworkManager stop
and
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
are what would have made NM stop changing your ip.
also killall dhclients / wpa_supplicants / pppoe daemons/ whatever else could be mesing with network settings.
and then also do the ifup/ifdown thing.

all in all, i guess uninstalling it is easier, if you're going the static route (that's not a really bad pun, i promise) :)

---

### Post by BC7333 on 2008-08-02
> **t.alex said:**
> your answer is in '/var/log/syslog'
take a look there
avahi daemon may be messing with your network. i always shut it down right from the beginning  :)

and how?

Using 0.7 here and avahi is loading per syslog 0.6.23

Sometimes network works fine,sometimes a bit flakey..

thx

---

### Post by t.alex on 2008-08-03
> **BC7333 said:**
> and how?

uninstall it, whenever possible :lolflag: i.e. if the dependences allow you or use 'services-admin' and disable it.

but avahi-daemon won't make your network go 'slower'. by "messing with your network" i meant creating routes/devices or assigning ip addresses to them behind my back without my knowledge

---

### Post by Peaceable Frood on 2008-08-03
I find network manager to be crap, I always remove it and just set up the connection manually.

---

### Post by BC7333 on 2008-08-03
> **Peaceable Frood said:**
> I find network manager to be crap, I always remove it and just set up the connection manually.

I did also and used WICD or wifi radar.

Pleasantly pleased with NM 0.7 though.. quite good so far.

---

### Post by caryb on 2008-08-03
> $ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0

Sorry guys but I'm confused! I might be a bit thin in my Linux knowledge but my routing knowledge is very strong, That config was not given by any router! If it was it would read this

> $ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet dhcp

That top config had to be entered manually, you just cant get a static address via dhcp! Even if you have a static registration in dhcp for a fixed IP it will still show as dhcp in the /etc/network/interfaces file.


Cary

---

### Post by xens on 2008-08-03
someone knows when NM 7.0 will be integrated into interpid ibex? Maybe into alpha 4 ?

---

