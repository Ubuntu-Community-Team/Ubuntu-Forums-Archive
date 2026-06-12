---
title: "Limited networking"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by robsan on 2005-09-08
Hey all,

I installed Ubuntu today and i'm having a weird problem with internet access:

The PC is wired to a DLink 502T router, and at first eth0 was configured for DHCP. The thing is, i can update packages, ping and resolve hosts, wget pages (for example [www.google.com)](www.google.com)), but Firefox and GAIM don't work! Firefox resolves the hostnames but eventually times out. Even so, i can access the router's page perfectly.

I've since set eth0 to static but the problem prevails..  :-?

--

ifconfig and route output:

```

rob@brazil:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:B8:FB:C6
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feb8:fbc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:652677 (637.3 KiB)  TX bytes:541992 (529.2 KiB)
          Interrupt:19 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:508742 (496.8 KiB)  TX bytes:508742 (496.8 KiB)

rob@brazil:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         dlink           0.0.0.0         UG    0      0        0 eth0
```

---

### Post by rafakl on 2005-09-09
try configuring the proxy options in Firefox

---

### Post by robsan on 2005-09-09
[QUOTE=rafakl]try configuring the proxy options in Firefox[/QUOTE]

 Hey, thanks for the reply.

 I obviously checked that, tried with "direct connection to the internet" and "automatically detect settings". GAIM is also correctly configured, i inicially thought it could be a problem connecting to ICQ/MSN's gateways but Jabber also doesn't connect.


 Anything else? Anyone? I really want to switch from windoze, so please help..  :-|

---

### Post by heimo on 2005-09-09
This is a weak guess (but if you don't anything else, you might try) - disable ipv6. 
Instructions:
[http://www.ubuntuforums.org/showpost.php?p=311362&postcount=2](http://www.ubuntuforums.org/showpost.php?p=311362&postcount=2)

Also disable ipv6 in Firefox, enter (as address): *about:config* type ipv6 as a filter and change network.dns.disableIPv6 to true (double click on it). Any change?

---

### Post by bdn01 on 2005-09-12
You're not alone. 

I have exactly the same issue.

Ping router - Fine!
Ping service provider via router (BT) - Fine!
Use Firefox to retrieve google - not fine !

I've also checked everything like you, even tried a static IP.

Any solutions ideas, anyone?

---

### Post by bdn01 on 2005-09-12
Another thread ([http://ubuntuforums.org/showthread.php?t=62631](http://ubuntuforums.org/showthread.php?t=62631)
) suggests... updating the resolv.conf file:

"If your router is IP address 192.168.0.1, then /etc/resolv.conf probably needs to contain: nameserver 192.168.0.1"

My router is on 192.168.1.1 so I'll try this later today. If you get anywhere in the mean-time please let me know.... 

Bdn

---

### Post by heimo on 2005-09-12
You can test if your router / gateway address can be used as a DNS, with
 ```
dig @192.168.0.1 ubuntu.com
``` 
where 192.168.0.1 is obviously the ip address of your router. It should return valid A record / ip address for ubuntu.com 

If it works, put it in resolv.conf - remove other lines with *nameserver *to test.

You may have a setting on your routers settings (probably web based configuration), something like DNS caching, DNS relay, DNS server...

---

### Post by bdn01 on 2005-09-12
I tried "dig @192.168.1.1 unbuntu.com" and this returns the IP address ok. I checked rseolv.conf and this has "nameserver 192.1668.1.1" so should be ok. The thing is firefox still doesn't respond. I tried typing the IP address in directly and this seemed to work (once). Any other ideas?

---

### Post by bdn01 on 2005-09-12
Solution: 

in firefox type "about:config"
in the filter enter "ipv6"
double click the 'disable ipv6' (boolean) so it's true

This worked for me, so far unless it's a coincidence.

---

### Post by robsan on 2005-09-13
I'm happy to say that disabling ipv6 both in aliases and firefox has given me access to the web. However, GAIM is still not connecting..

---

### Post by votd on 2005-09-23
hi guys,
I have exactly the same problem... Firefox works fine (with ipv6 disabled), ping, wget is also ok... but GAIM doesnt connect and Synaptic neither.

By the way I m using an ASUS wireles DSL router... 

Any suggestions?

---

### Post by bdn01 on 2005-09-24
Nope. I've tried numerous things. Almost given up trying to fix it, I can't get evolution to pick up mail, synaptic to work or ipodder to get new episodes, xmms works fine with radio streams though.

  ---- HELP ---- 

 Should/can we point this thread to the hardcore support community?  

  ---- HELP ----

---

### Post by tek on 2005-09-24
[QUOTE=heimo]This is a weak guess (but if you don't anything else, you might try) - disable ipv6. 
Instructions:
[http://www.ubuntuforums.org/showpost.php?p=311362&postcount=2](http://www.ubuntuforums.org/showpost.php?p=311362&postcount=2)

Also disable ipv6 in Firefox, enter (as address): *about:config* type ipv6 as a filter and change network.dns.disableIPv6 to true (double click on it). Any change?[/QUOTE]

Thought you would like to know:  works perfectly!!!!!

---

### Post by bdn01 on 2005-09-25
I read and applied the suggestions in this thread today, things seem to have improved. 

[http://ubuntuforums.org/archive/index.php/t-171.html](http://ubuntuforums.org/archive/index.php/t-171.html) 


I'd previously commented out the 'pf-10 ipv6' line and add a new line with 'pf-10 off' so that I could revert easily. After removing the commented line and renaming the ipv6.ko file I can get iPodder to work. I'll need to test the other applications, but this is definitely a good sign.

---

### Post by votd on 2005-09-25
hey i've solved it...
I dont know exactly which step solved the problem, I did several things..
I first installed 3 packages, cuz i read somewhere to do so :)
resolvconf
pump
dnsmasq

It is said to solve also some general networking problems in ubuntu. But after installing these, my problem was still there... then I ve edited resolv.conf one more time, added DNS servers of my ISP (formerly it was my router address, - ok ok, I know I should do it at the beginning - ) and now everything works fine!

---

### Post by bdn01 on 2005-09-26
Yeee-haaa! That works. Is all that really necessary or just the resolv.conf changes. I read somewhere today that this issue may only exist for BT broadband users?

---

### Post by robsan on 2005-11-29
Ok, after a long time i've returned to Ubuntu, since i had so many troubles getting internet to work with some apps i just gave up! But Windows sucks and i gave it another shot! So here's what happened:

 - i tried kubuntu, strangely after disabling ipv6 in "aliases" and kde enviroment everything worked fine!

 - i wasn't happy with with kde (sorry to the afficionados out there), so i installed regular ubuntu

 - same problems occured, until i noticed that even though i changed resolv.conf it was being reverted to the router's ip

 - i configured a static address for eth0 and.. after that all went ok!

 - yayyyyy!! ;)

 I figure that using dhcp was just updating resolv.conf with the router's address. But now all is ok, which is great, since i was considering switching routers!


p.s. - ubuntu rules ;)

---

