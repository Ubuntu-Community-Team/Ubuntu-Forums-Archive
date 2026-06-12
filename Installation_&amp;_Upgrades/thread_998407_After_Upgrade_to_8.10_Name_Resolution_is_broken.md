---
title: "After Upgrade to 8.10 Name Resolution is broken"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by DantePasquale on 2008-11-30
Hi All,

I upgraded my server to 8.10 today and things looked really good. Unfortunately, name resolution is no longer working! Here's some info:

 2.6.27-10-generic #1 SMP Fri Nov 21 19:19:18 UTC 2008 x86_64 GNU/Linux

I am running ISPConfig with it's own DNS. When I lookup one of my domains against my own name server things work fine:

```
dig @localhost www.cocoanet.us

; <<>> DiG 9.5.0-P2 <<>> @localhost www.cocoanet.us
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38226
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;www.cocoanet.us.		IN	A

;; ANSWER SECTION:
www.cocoanet.us.	86400	IN	A	74.1.46.163

;; AUTHORITY SECTION:
cocoanet.us.		86400	IN	NS	inferno.cocoanet.us.

;; ADDITIONAL SECTION:
inferno.cocoanet.us.	86400	IN	A	74.1.46.162

;; Query time: 1 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun Nov 30 19:03:30 2008
;; MSG SIZE  rcvd: 87
```


However when hitting outside of my DNS nothing seems to work.
```
dig www.cocoanet.us

; <<>> DiG 9.5.0-P2 <<>> www.cocoanet.us
;; global options:  printcmd
;; connection timed out; no servers could be reached
```

here's my resolv.conf:
```

domain cocoanet.us
nameserver 64.105.179.138
nameserver 64.105.189.26
nameserver localhost
search cocoanet.us
```

Also, I removed the Network-Manager packages because they kept wiping out my resolv.conf, but when I replaced it with the proper file, things worked OK. But I can't get it to resolve at all with the proper resolv.conf without the network manager packages.

I also removed apparmor thinking that may have something to dow with what's going on but no luck.

Also, if I dig against my DNS with someone elses domain here's what I get:

```
dig @localhost www.covad.com

; <<>> DiG 9.5.0-P2 <<>> @localhost www.covad.com
; (1 server found)
;; global options:  printcmd
;; connection timed out; no servers could be reached
```

and here's what's in syslog:
```
Nov 30 18:54:44 inferno named[14089]: too many timeouts resolving 'www.grand-am.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:44 inferno named[14089]: too many timeouts resolving 'mail-sfbay.sun.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'addons.mozilla.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'blogs.manageengine.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'www.google-analytics.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'feedproxy.google.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'fashionlegwear.blogspot.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'fb.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:45 inferno named[14089]: too many timeouts resolving 'images.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:46 inferno named[14089]: too many timeouts resolving 'ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:46 inferno named[14089]: too many timeouts resolving 'traffic.adventnet.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:46 inferno named[14089]: too many timeouts resolving 'evintl-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:46 inferno named[14089]: too many timeouts resolving 'evsecure-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'en-us.www.mozilla.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'js.zohostatic.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'mail-sfbay.sun.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'addons.mozilla.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'blogs.manageengine.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'www.google-analytics.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:47 inferno named[14089]: too many timeouts resolving 'feedproxy.google.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:48 inferno named[14089]: too many timeouts resolving 'fashionlegwear.blogspot.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:48 inferno named[14089]: too many timeouts resolving 'fb.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:48 inferno named[14089]: too many timeouts resolving 'images.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:48 inferno named[14089]: too many timeouts resolving 'ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'traffic.adventnet.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'evintl-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'evsecure-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'en-us.www.mozilla.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'js.zohostatic.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'mail-sfbay.sun.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'addons.mozilla.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:49 inferno named[14089]: too many timeouts resolving 'blogs.manageengine.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:50 inferno named[14089]: too many timeouts resolving 'www.google-analytics.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:50 inferno named[14089]: too many timeouts resolving 'feedproxy.google.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:50 inferno named[14089]: too many timeouts resolving 'docs.kde.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:50 inferno named[14089]: too many timeouts resolving 'fb.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:50 inferno named[14089]: too many timeouts resolving 'images.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:51 inferno named[14089]: too many timeouts resolving 'www.photography-lighting.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:51 inferno named[14089]: too many timeouts resolving 'traffic.adventnet.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:51 inferno named[14089]: too many timeouts resolving 'evintl-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:51 inferno named[14089]: too many timeouts resolving 'evsecure-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:51 inferno named[14089]: too many timeouts resolving 'en-us.www.mozilla.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:51 inferno named[14089]: too many timeouts resolving 'js.zohostatic.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:52 inferno named[14089]: too many timeouts resolving 'mail-sfbay.sun.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:52 inferno named[14089]: too many timeouts resolving 'addons.mozilla.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:52 inferno named[14089]: too many timeouts resolving 'blogs.manageengine.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:52 inferno named[14089]: too many timeouts resolving 'www.google-analytics.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:52 inferno named[14089]: too many timeouts resolving 'feedproxy.google.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:52 inferno named[14089]: too many timeouts resolving 'docs.kde.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:53 inferno named[14089]: too many timeouts resolving 'fb.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:53 inferno named[14089]: too many timeouts resolving 'images.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:53 inferno named[14089]: too many timeouts resolving 'www.photography-lighting.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:53 inferno named[14089]: too many timeouts resolving 'traffic.adventnet.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:54 inferno named[14089]: too many timeouts resolving 'evintl-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:54 inferno named[14089]: too many timeouts resolving 'evsecure-ocsp.verisign.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:54 inferno named[14089]: too many timeouts resolving 'en-us.www.mozilla.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:54 inferno named[14089]: too many timeouts resolving 'mail-sfbay.sun.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:55 inferno named[14089]: too many timeouts resolving 'docs.kde.org/A' (in '.'?): disabling EDNS
Nov 30 18:54:55 inferno named[14089]: too many timeouts resolving 'fb.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:55 inferno named[14089]: too many timeouts resolving 'images.howtoforge.com/A' (in '.'?): disabling EDNS
Nov 30 18:54:56 inferno named[14089]: too many timeouts resolving 'www.photography-lighting.com/A' (in '.'?): disabling EDNS
```
 

Ideas anyone?

Also, covad's DNS is OK as I'm connecting through the same network with my laptop.

Oh, and wireshark shows DNS request going out and a proper response coming back! I can't figure out why this isn't getting to the applications!

--------------------

OK. Here's what I have done and noticed so far. I use multiple Virtual IP's (MultiHosted) on 2 NICS in the server. Here's my **/etc/network/interfaces** file:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 74.1.46.162
netmask 255.255.255.240
gateway 74.1.46.161

iface eth0:1 inet static
address 74.1.46.163
netmask 255.255.255.240
gateway 74.1.46.161

iface eth0:2 inet static
address 74.1.46.164
netmask 255.255.255.240
gateway 74.1.46.161

iface eth0:3 inet static
address 74.1.46.165
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1 inet static
address 74.1.46.166
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:1 inet static
address 74.1.46.167
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:2 inet static
address 74.1.46.168
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:3 inet static
address 74.1.46.169
netmask 255.255.255.240
gateway 74.1.46.161

iface eth1:4 inet static
address 74.1.46.174
netmask 255.255.255.240
gateway 74.1.46.161


auto eth0
auto eth0:1
auto eth0:2
auto eth0:3
auto eth1
auto eth1:1
auto eth1:2
auto eth1:3
auto eth1:4
```

So after installation, no traffic whatsoever was on eth1 or any IP's on eth1. Nothing going out either.

So I re-installed Network-Manager and removed my /etc/network/interfaces file. Created the entries for eth0 and eth1 in Network-Manager and rebooted. Lo and behold, both eth0 and eth1 had IP addresses and traffic and now name resolution works even though my **/etc/resolv.conf** is now empty.

For the life of me, I cannot figure out how to add VIPs using that Network-Mangler interface! So I just did:

```
sudo ifconfig  eth0:1 74.1.46.163/28
sudo ifconfig  eth0:2 74.1.46.164/28
sudo ifconfig  eth0:3 74.1.46.165/28
sudo ifconfig  eth1:1 74.1.46.167/28
sudo ifconfig  eth1:2 74.1.46.168/28
sudo ifconfig  eth1:3 74.1.46.169/28
```

Now ifconfig -a shows these guys are up and running!
[B]
Now, how do I make this survive reboots[/B]??????????? Since /etc/network/interfaces no longer works!!!!!!

---

