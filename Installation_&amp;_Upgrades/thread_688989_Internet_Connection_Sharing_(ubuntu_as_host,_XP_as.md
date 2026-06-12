---
title: "Internet Connection Sharing (ubuntu as host, XP as client)"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by m4n40 on 2008-02-05
Hi all, 

I found some tutorial explaining how to do this in the other way (xp as host). Could someone walk me through the methode to share the internet connection of my ubuntu computer to a xp laptop, knowing that i don t whant to change the tcpip configuration of the xp machine as i run the host on ubuntu and xp and the connection sharing is already working proply under windows. 
Ps i can t buy hub or router or whatever very easily as i live in china in a pretty remote place and the first computer shop that might sell those is at one 2 hours by bus.. 

Thanks all for your help ~

---

### Post by hyperair on 2008-02-06
Try installing Firestarter from Synaptic. There are configuration options to share your internet connection there.

---

### Post by m4n40 on 2008-02-06
thanks hyperair i have tried that but when i wanna start fisresarter i get the message: failed to start, the eth0 is not active. But i did the raspppoeconf and my internet works proply. Do you have any idee where that might come from ?

---

### Post by hyperair on 2008-02-06
Please run this command: "ifconfig" and post the output please. You might like to blank out your MAC addresses and IP addresses while you're at it. I don't see how, but it seems that the information can be used to hack =\

---

### Post by hyperair on 2008-02-06
Let me guess, you configured eth0 as the interface where you're going to share your connection, but eth0 isn't connected to anything? I'm afraid you can't leave it on unless that network interface is connected to another computer first.

---

### Post by nilarimogard on 2008-02-06
I used something i found somewhere on this forums (don't remember where, but i saved the text on my PC). Here it is:



The following will explain how to share your Internet connection:

Note: Type all the following commands in a root terminal, DO NOT use sudo.

1. Start by configuring the network card that interfaces to the other computers on you network:

# ifconfig ethX ip

where ethX is the network card and ip is your desired server ip address (Usually 192.168.0.1 is used)

2. Then configure the NAT as follows:

# iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE

where ethX is the network card that the Internet is coming from

# echo 1 > /proc/sys/net/ipv4/ip_forward

3. Install dnsmasq and ipmasq using apt-get:

# apt-get install dnsmasq ipmasq

4. Restart dnsmasq:

# /etc/init.d/dnsmasq restart

5. Reconfigure ipmasq to start after networking has been started:

# dpkg-reconfigure ipmasq

6. Repeat steps 1 and 2.

7. Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf

# gedit /etc/sysctl.conf

8. Reboot. (Optional)

I hope this helps.

---

### Post by m4n40 on 2008-02-06
Thx all for your answers, hyperair here is my ifconfig log, And nilarimogard could you tell me how to run directly the root concole? Wont this work if i use the sudo ?

eth0      Link encap:Ethernet  HWaddr 00:17:31:B6:70:2B  
          inet6 addr: fe80::217:31ff:feb6:702b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4031292 (3.8 MB)  TX bytes:383563 (374.5 KB)
          Interrupt:17 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:4D:04:59  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe4d:459/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:926 (926.0 b)  TX bytes:3775 (3.6 KB)
          Interrupt:19 Base address:0xac00 

eth0:avah Link encap:Ethernet  HWaddr 00:17:31:B6:70:2B  
          inet addr:XXX.XXX.XXX.XXX  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3977 (3.8 KB)  TX bytes:3977 (3.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:XX.XX.XXX.XXX  P-t-P:219.128.64.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3061 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3953195 (3.7 MB)  TX bytes:300484 (293.4 KB)

---

### Post by nilarimogard on 2008-02-06
Well it says not to use sudo. I think i went to Applications > System Tools > Root Terminal.

---

### Post by boohickey11 on 2008-02-22
I followed this thread to get internet connection sharing on my Kubuntu machine to share with a Mac.  It works but I have to rerun the commands every time I restart the computer.  Any ideas?

---

### Post by hyperair on 2008-02-22
@m4n40: Try using ppp0 as your internet connection interface.

---

### Post by nilarimogard on 2008-02-22
Or you could write the commands in a .sh and add it to startup.

---

### Post by boohickey11 on 2008-02-22
> **nilarimogard said:**
> Or you could write the commands in a .sh and add it to startup.

Well, it seemed that the line that gets the sharing to work again is

# dpkg-reconfigure ipmasq

So if this helps to understand whats wrong?  Also, the tutorial never describes what choices to make when you run this.  Does it matter?

---

### Post by nilarimogard on 2008-02-23
I don't know what's wrong unfortunately, but as i said, you can add that line in a blabla.sh file, then chmod +x blabla.sh and then go to System > Preferences > Sessions and add it to startup programs. That untill you can fix it for good...

P.s.: did you add a static Ip for the local newtwork (eth1), for instance 192.168.0.1 and the other computer 192.168.0.2 ... maybe it assigns a new ip on each boot and that could be the problem, having a static ip would prevent that. I don't know, i'm just trying to guess...

---

### Post by boohickey11 on 2008-03-06
I've installed GuardDog as my firewall. Does anyone know what ports/protocols need to be open so that this method of ICS works.

---

