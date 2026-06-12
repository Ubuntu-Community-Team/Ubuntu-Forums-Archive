---
title: "Help with Server Installation using DHCP"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by new2lynux on 2008-04-12
I recently bought a computer with the intension of making it a linux server. I am migrating from windows to linux and I can say that I am loving it.

My computer system is as follows: Intel Core 2 Duo CPU @ 2.20GHz. 3.00GB RAM. hp Pavillion. VirginMediaUK is my ISP. My router is Dynamode BR6004 W-G1.

I followed the documentation on the ubuntu website to do the installation with some hitches primarily with the installation of the MySQL. I did the installation this time with success.

Everything is ok when I boot the system except the DHCP-server which says FAIL during on booting.

Also during installation, the system could not get my ip address using DHCP. My ISP is Virgin Media UK. I called them and they said that they use DHCP IP allocation but NOT Static and refered me to their free webspace service which can't serve my needs.

Ping fails. I have pinged [www.google.com](www.google.com) and virgin media itself but it says it can't find the host.

Can anyone tell me the solution to this problem? I tried with the IP address, DNS, gateway, mask, etc I get when I connect with the computer when boot in Windows Vista but without success. shows on my system IPv4. I really need help.

---

### Post by kaginken on 2008-04-12
Post your results of
```
ifconfig
```

If you're behind your router - your ISP can't help you much.  Your ISP only assigned your routers IP.  You possibly may need to tweak your router and/or test connectivity from another machine behind the router.

Can you ping your router?

---

### Post by new2lynux on 2008-04-16
Update: Now ping works but only sometimes. What I find out is that when I boot the pc before plugging in the LAN cable it works sometimes but not always. It has never worked when plugged in on booting. I never have problems whn I boot in VISTA. I have tried working out some logic in the config files. It is working as at this time... and I hope it does forever.

I have set up my router to assign a particular IP to my MAC address. I have set up my website and replaced the default apache page with mine. I get the webpage when I use the IP in my network. I have setup an account with DynDNS. My router supports DynDNS so I have added my account there. I have added the hostname to the ServerName within the <VirtualHost> tags. 

One problem still remains: I can't access my web page from outside my network. After configuring my router in the port forwarding so that my webservers IP has port 80, I get a message from firefox on the status bar saying "waiting for mywebpage.homelinux.com" but the page never loads. Any other router configuration (eg. changing etc/apache2/port.conf to listen to some other port and adding this to my router) gives me the message on the firefox status bar "connecting to mywebpage.homelinux.com."

How can I resolve this?

---

### Post by new2lynux on 2008-04-16
thanks

---

### Post by new2lynux on 2008-04-16
see next post

---

### Post by new2lynux on 2008-04-16
```
new2lynux@exedus:~ ifconfig

 eth0   Link encap:Ethernet HWaddr 00:1E:8C:6E:F1:6B
          inet addr:192.168.1.2 Bcast:192:168:1.255 Mask:255.255.255.0
          inet6 addr: fe80: :21e:8cff:fe6e:f16b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST:1500 Metric:1
          RX packets:8938 errors:0 dropped:4212071010 overruns:0 frame:0
          TX packets:1805 errors:0 droppped:0 overruns:0 varriers:0
          collisions:0 txqueuelen:1000
          RX bytes:2261738 (2.1 MB) TX bytes:157062 (153.3 KB)
          Interrupts:18

lo       Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:1263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:425480 (415.5 KB) TX bytes:425480 (415.5 KB)
```

---

