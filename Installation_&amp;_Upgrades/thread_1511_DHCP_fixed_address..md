---
title: "DHCP fixed address."
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by Einherjar on 2004-10-21
My new brand Ubuntu gets a different IP address from the DHCP server everytime it boots or the network is restarted. I have tried to modify the /var/run/dhclient.leases &amp; /etc/dhclient,conf files to force a fixed IP address assignment... with no luck.

   What am I missing here?

---

### Post by cybrjackle on 2004-10-21
If you just want to give it a static

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)

Section

 10.6.1 Configuring an interface with a static IP address

The jist of it, edit /etc/network/interfaces and change your ethX to whatever your settings are, example
```

iface eth0 inet static
address 192.168.0.111
netmask 255.255.255.0
gateway 192.168.0.1

```

To find your settings.  ifconfig will probably show "eth0" with and ip addr.
```

$ ifconfig
eth0      Link encap&#58;Ethernet  HWaddr 00&#58;E0&#58;81&#58;61&#58;B2&#58;21
          inet addr&#58;192.168.1.106  Bcast&#58;192.168.1.255  Mask&#58;255.255.255.0
          inet6 addr&#58; fe80&#58;&#58;2e0&#58;81ff&#58;fe61&#58;b221/64 Scope&#58;Link
          UP BROADCAST RUNNING MULTICAST  MTU&#58;1500  Metric&#58;1
          RX packets&#58;233291 errors&#58;0 dropped&#58;0 overruns&#58;0 frame&#58;0
          TX packets&#58;294716 errors&#58;0 dropped&#58;0 overruns&#58;0 carrier&#58;0
          collisions&#58;0 txqueuelen&#58;1000
          RX bytes&#58;125168141 &#40;119.3 MiB&#41;  TX bytes&#58;25624438 &#40;24.4 MiB&#41;

```

My ip is **192.168.1.106** netmask **255.255.255.0** 

```

$ ip route list
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.106
default via 192.168.1.1 dev eth0

```
gateway **192.168.1.1**

So I end up with the following:

```

iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1

```

---

### Post by Einherjar on 2004-10-22
I can't have a static IP address. There are no pools of reserved addresses and I don't want to cause any trouble if the DHCP server assigns my IP address.

   There's a machine that acts as a NAT device, providing unrestricted Internet access. Since my IP tends to be constantly changing (the NAT device looks for my machine's name, not my MAC address), the NAT device doesn't perform my IP translation.

   I'd like to be able to 'force' the DHCP to assign me a fixed-address but, somehow, I'm missing something.

---

### Post by cybrjackle on 2004-10-22
[quote=Einherjar]I can't have a static IP address. There are no pools of reserved addresses and I don't want to cause any trouble if the DHCP server assigns my IP address.

   There's a machine that acts as a NAT device, providing unrestricted Internet access. Since my IP tends to be constantly changing (the NAT device looks for my machine's name, not my MAC address), the NAT device doesn't perform my IP translation.

   I'd like to be able to 'force' the DHCP to assign me a fixed-address but, somehow, I'm missing something.[/quote]

You don't want static but you want DHCP to be forced to assign you a fixed-address? 

I assume your at work and not home with this box or something like that?

Why do you have to have a fixed/static address, what is the overall goal your trying to achieve?

---

### Post by FLeiXiuS on 2004-10-22
If you are at home, and your running a 192.168.1.0 network and you have no more then 253 computers on your network, then your just fine to give a static address of, 192.168.1.254.  This won't conflict with your current DHCP.

If your at work or do not have any addresses available, then you won't beable to setup a static IP.  The DHCP server will provide you with an IP that is available next in the IP pool.

---

### Post by Einherjar on 2004-10-22
[color=green]You don't want static but you want DHCP to be forced to assign you a fixed-address? [/color]

   No, I cannot have a static IP address because I don't want to risk to interfere with the pools asigned by the DHCP server. If I choose the wrong address, I might be in some trouble with the boss.

   Whenever I boot any operating system (Windows 2000, Windows XP, Windows 2003 Server, Fedora Core 1 &amp; 2, Suse 9.1, FreeBSD 5.2.1, etc) the DHCP server always assigns the **same IP address**, no matter how many times y reboot the machine or restart the networking processes.

  Somehow, the DHCP server and my Ubuntu box doesn't seem to like each other, and I keep geeting different addresses on each bootting.

[color=green]I assume your at work and not home with this box or something like that? [/color]

   That's right. The Ubuntu box is my current O.S. at work.

[color=green]Why do you have to have a fixed/static address, what is the overall goal your trying to achieve?[/color]

   Not everyone here is allowed to get Internet access. So certain addresses are translated in the NAT device in order to get into the Net. Those addresses are checked by DNS queries (my box is named Einherjar and used to have one and only one IP address assigned by the DHCP server. Not anymore...) and, since Ubuntu is my O.S., my IP is constantly changing. So the NAT device can't keep track of me.

   I don't know why Ubuntu is behaving like this while **all** my other O.S.es worked like a charm, getting me the same IP address.

---

### Post by cybrjackle on 2004-10-22
> **Einherjar][color=green]You don't want static but you want DHCP to be forced to assign you a fixed-address? [/color]

   No, I cannot have a static IP address because I don't want to risk to interfere with the pools asigned by the DHCP server. If I choose the wrong address, I might be in some trouble with the boss.

   Whenever I boot any operating system (Windows 2000, Windows XP, Windows 2003 Server, Fedora Core 1 &amp said:**
> I assume your at work and not home with this box or something like that? [/color]

   That's right. The Ubuntu box is my current O.S. at work.

[color=green]Why do you have to have a fixed/static address, what is the overall goal your trying to achieve?[/color]

   Not everyone here is allowed to get Internet access. So certain addresses are translated in the NAT device in order to get into the Net. Those addresses are checked by DNS queries (my box is named Einherjar and used to have one and only one IP address assigned by the DHCP server. Not anymore...) and, since Ubuntu is my O.S., my IP is constantly changing. So the NAT device can't keep track of me.

   I don't know why Ubuntu is behaving like this while **all** my other O.S.es worked like a charm, getting me the same IP address.

I'm sorry, but I must be the only one getting confused here, it seems to me that you keep saying the same thing over and over, you need static but you can't have it, your NAT needs to keep track of you by IP but you don't want to set a static ip.  I understand that you are saying Ubuntu seems to be the only distro that changes your addr. but if you need to keep the same IP for NAT and your talking workstations not servers, the worst that can happen from statically assigning your self and IP from a DHCP server is that someone else wont get it when your on.

---

### Post by Einherjar on 2004-10-22
[color=green]the worst that can happen from statically assigning your self and IP from a DHCP server is that someone else wont get it when your on[/color]

   Not exactly. Until the DHCP server assigns me a IP address (I have to provide the hostname, otherwise it won't get me an IP), the DNS server doesn't have an entry for me. Don't ask me why they behave like this, because I don't know.

   So, if I get myself a static IP address, the DNS won't respond when queried about the machine named Einherjar and the NAT device won't let me get access to the Net.

   PS. Forgive my many mistakes, but English is not my native language.

---

### Post by cybrjackle on 2004-10-22
Your fine, I'm just trying to figure out why it would do that. :P

Have you atleast tried to set /etc/network/interfaces with something like

iface eth0 inet static
address 192.168.1.106
netmask 255.255.255.0
gateway 192.168.1.1 

Only with your ip info and reboot to see what DNS/NAT/NETWORK will do?

---

### Post by Einherjar on 2004-10-22
I'll give it a try next Monday. Thank you.   :wink:

---

