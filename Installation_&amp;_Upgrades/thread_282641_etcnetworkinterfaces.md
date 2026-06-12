---
title: "/etc/network/interfaces"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2006-10-23
Hey
I have test to run my own scripts in rc.local but it doesnt startup good.
So now i have decided to do this is in /etc/networ/interfaces.
Hope it works as i want, something like this.

If iwlist scan |grep xxxxx-school 
then it connect to it and get all from dhcpd. on eth1.

If it not found that network it set eth0 wierd connection:
IP 192.168.0.5
ROUTE 192.168.0.1
DNS/NAMESERVER 192.168.0.100


How can i make this, you have any smart solution?

---

### Post by Jussi Kukkonen on 2006-10-23
You'll probably be able to do this with the *mapping* section of the file. I'll attach what I had in use when I moved my laptop from a network to another. It worked flawlessly, but you might want to do it a little differently: my approach tries to setup a network and ping a router to find  out which network we are in, your situation might be simpler as you can just do that grep instead of the ping-places script...

```
# Guess the location of the machine by pinging gateway machines.
# Map eth0 to the interface where we get a ping.
mapping eth0
        script /etc/network/ping-places.sh
        map 192.168.0.101/24 192.168.0.1 eth-home
        map 130.233.136.137/24 130.233.136.254 eth-hut

# This is a list of hotpluggable network interfaces.
mapping hotplug
        script grep
        map eth0

iface eth-home inet static
        address 192.168.0.101
        netmask 255.255.255.0
        gateway 192.168.0.1

iface eth-hut inet static
        address 130.233.136.137
        netmask 255.255.255.0
        gateway 130.233.136.254

```
The ping-places scriptlooks like this:
```

#!/bin/sh

if [ `id -u` -ne 0 ] || [ "$1" = "" ]; then exit 1; fi

if [ -x /usr/bin/fping ]; then
        PING="/usr/bin/fping"
else
        PING="/bin/ping -c 2"
fi
iface="$1"
which=""
while read addr pingme scheme; do
        if [ "$which" ]; then continue; fi

        ip addr add $addr dev $iface  >/dev/null 2>&1
        ip link set $iface up         >/dev/null 2>&1

        if $PING $pingme >/dev/null 2>&1; then
                which="$scheme"
        fi
        ip link set $iface down       >/dev/null 2>&1
        ip addr del $addr dev $iface  >/dev/null 2>&1
done

if [ "$which" ]; then echo $which; exit 0; fi
exit 1

```

It's been a while since I put that up, so I can't help much... Read the man pages of *interfaces*.

---

### Post by dmsn on 2006-10-23
Nice i will test this later ;)

---

### Post by dmsn on 2006-10-23
dmsn@lappen:/etc/network$ cat interfaces
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

dmsn@lappen:/etc/network$

Please when i reboot it take so long time for gnome to start.
What can the problem be ?

---

### Post by RikoW on 2006-10-23
> **dmsn said:**
> dmsn@lappen:/etc/network$ cat interfaces
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

dmsn@lappen:/etc/network$

Please when i reboot it take so long time for gnome to start.
What can the problem be ?

I had the same problem until recently. Apparently, I screwed up my interfaces file, when I played around with the attempt to have the right network interface configured on start-up.

try to add *auto lo* to the section for your loop-back device:

```
# The loopback network interface
auto lo
iface lo inet loopback

```

Cheers,

              Riko

---

### Post by dmsn on 2006-10-23
wehooo finally ;=)

Big thanks to Riko!

---

### Post by dmsn on 2006-10-23
Hey
I wonder if anyone know how i can add dns servers to this interfaces file.
I searched on google and man interfaces but didnt found it out, but i know
it works i have seen it.
So bad to add always in resolv.conf.


thanks

---

### Post by dmsn on 2006-10-23
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
dns-domian 192.168.0.1

auto eth1
iface eth1 inet dhcp
wireless-essid XXXXXXXX
wireless-key YYYYYYYYYYY

I have test with dns-domain and dns-nameservers
nothing work here :/
The problem is when i go to school and connect to their wlan
and on evning home connections the dns from school is still there and i have to manual add a dns in resolv.conf.


Please help me out, thanks.

---

### Post by troyaner on 2008-02-17
replace the "a"
dns-dom**_ai_**n 192.168.0.1

try one of this
#dns-nameserver 192.168.0.1
#dns-nameservers 192.168.0.1 192.168.0.2
#dns-search somedomain.org
#dns-domain 192.168.0.1

---

