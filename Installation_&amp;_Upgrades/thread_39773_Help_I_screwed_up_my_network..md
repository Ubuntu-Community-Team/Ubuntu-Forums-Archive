---
title: "Help I screwed up my network."
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by Jonas82 on 2005-06-06
Hi,

I am running Ubuntu as server. I need help for setting up IP/DNS etc. What files and commands to use?

Thank you.

---

### Post by lt_kije on 2005-06-06
Can you post a bit more information about what you're trying to do? Do you need to assign an IP address to the Ubuntu server statically or dynamically (DHCP)? Is the Ubuntu server your network's gateway? What's the server supposed to do (HTTP/DHCP/DNS...)?

lt_kije

---

### Post by Jonas82 on 2005-06-06
Thank you for replying.

The server is a http server.

It should just get a static ip.

---

### Post by lt_kije on 2005-06-06
To assign a static IP, you can use the following command:
```

$ sudo ifconfig eth0 192.168.0.1

```

Where eth0 is the network interface for which you want to set the static IP address and 192.168.0.1 is the IP address you'd like to give it.

I'm not sure if you actually want to set the IP that way though -- what do you mean by "get a static IP"? Do you want it assigned automatically by a router or set on boot by the server itself?

lt_kije

---

### Post by Jonas82 on 2005-06-06
I got a static ip from my provider, that the server should use on boot.

---

### Post by Jonas82 on 2005-06-06
Is there some kind of console program in ubuntu to setup the network?

---

### Post by lt_kije on 2005-06-06
[QUOTE=Jonas82]I got a static ip from my provider, that the server should use on boot.[/QUOTE]
 You should then just have to run the command I supplied above to set the server to that IP.

---

### Post by lt_kije on 2005-06-06
[QUOTE=Jonas82]Is there some kind of console program in ubuntu to setup the network?[/QUOTE]
 ifconfig is the standard Unix network config utility. It'll do what you need it to do.

If you want the IP address set on boot, edit the file /etc/network/interfaces and add a line similar to the following:
```

iface eth0 inet static 
      address 192.168.0.1

```

And substitute the correct IP for 192.168.0.1.

Read the man page for 'interfaces'; you'll need to add the netmask and possibly the gateway info as well. These should be supplied by your ISP.

lt_kije

---

### Post by Jonas82 on 2005-06-06
Thanks alot. I will give it a try.

---

### Post by Jonas82 on 2005-06-06
auto eth0
iface eth0 inet static
        address x.x.x.x
        netmask 255.255.255.0
        gateway x.x.x.x

This seems to work. Thanks again.

---

### Post by Jonas82 on 2005-06-06
Ok, I was a little too fast. It works on the internal network(192.168.1.x), but I cant´t resolve dns, or ping internet IP´s from the server.

---

### Post by rsgooch on 2005-06-07
You will also need to modify your /etc/resolv.conf and put your domain and dns server information.

Here is an example:

search yourdomain.com
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
...




Hope this helps
RG

---

### Post by Jonas82 on 2005-06-08
I dont have a domain, so what should be in the search? My files look like this:

> /etc/resolv.conf
nameserver 212.242.40.3
nameserver 212.242.40.51

> /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
	script grep
	map eth0

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.26
	netmask 255.255.255.0
#	network 192.168.1.0
#	broadcast 192.168.0.255
	gateway 192.168.1.1
#iface eth0 inet dhcp

> root@jonasl:~ # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:B5:3A:54
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:feb5:3a54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6941 (6.7 KiB)  TX bytes:6173 (6.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

This is from a winXP machine that is working on the same network.
> Windows IP Configuration

        Host Name . . . . . . . . . . . . : jonas
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Physical Address. . . . . . . . . : 00-11-D8-95-7B-49
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.5
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 212.242.40.3
                                            212.242.40.51

From the winXP machine I can ping the Ubuntu machine, and internet ips. The ubuntu machine cant ping anything but localhost.

I am seriously lost on this.

---

