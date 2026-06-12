---
title: "Can connect to network, but can't get internet"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by diafygi on 2009-02-20
I downloaded and installed Jaunty Jackalope 9.04, but I've been unable to access the internet for each version I've downloaded (latest was 9/18/09 daily build).

Here's the scenario:
-Network Manager sees a connection and connects to it just fine.
-When you try to open any website (Ex. google.com) it gives an error that the server cannot be found.
-Other programs that access the internet cannot connect either (i.e. pidgin, synaptic, etc.)
-EXCEPT ping. When you ping a website (Ex. google.com), it responds! Crazy!

What the hell is going on. I'm connected, but everything I've tried except ping doesn't seem to think I'm connected.

I've filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/329937"), but nobody has responded. I would really like to be able to connect and download updates. Downloading the daily build is really getting annoying.

---

### Post by ronacc on 2009-02-20
do you by anychance have to blacklist IPV6 to access the net ?

---

### Post by diafygi on 2009-02-20
> **ronacc said:**
> do you by anychance have to blacklist IPV6 to access the net ?

Dunno, is there a command to test this?

---

### Post by ronacc on 2009-02-20
never mind ,if you don't know , you weren't using it . If you didn't have to do it before you wouldn't need to now .

---

### Post by diafygi on 2009-02-21
Okay, so I compared the ifconfig outputs for Jaunty and Intrepid.

Jaunty:```
eth0 Link encap:Ethernet HWaddr 00:90:f5:54:07:11
          inet6 addr: fe80::290:f5ff:fe54:711/64 Scope:Link
          UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7969 (7.9 KB) TX bytes:6719 (6.7 KB)
          Interrupt:17

lo Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet HWaddr 00:19:d2:52:b9:1d
          inet addr:192.169.1.100 Bcast:192.169.1.255 Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe52:b91d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34889 (34.8 KB) TX bytes:26924 (26.9 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-19-D2-52-B9-1D-39-31-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
```

Intrepid:```
eth0      Link encap:Ethernet  HWaddr 00:90:f5:54:07:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:52:b9:1d  
          inet addr:192.169.1.100  Bcast:192.169.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe52:b91d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1296181 (1.2 MB)  TX bytes:288279 (288.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-52-B9-1D-39-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

As you can see, there's nothing really different between the two. How do all the programs except ping not see that I am connected to a network?

---

### Post by ronacc on 2009-02-21
I see you have both eth0 and wlan0 do both of them not work or only one of them ?

---

### Post by diafygi on 2009-02-21
> **ronacc said:**
> I see you have both eth0 and wlan0 do both of them not work or only one of them ?

Yes, I've tried both connecting to my router via wireless and wired connections. It works fine both ways in Intrepid.

---

### Post by diafygi on 2009-02-21
Okay, so I figured out I can connect and display to my router's interface (192.168.1.1). Doesn't that mean it's a routing/dhcp issue? If so, why does ping work when other programs don't?

---

### Post by caryb on 2009-02-21
Can you resolve ip's via dns? I.E. ping google.com or can you only ping 192.168.0.254 for example? Might be a problem with your /etc/resolv.conf


Cary

---

### Post by diafygi on 2009-02-21
> **caryb said:**
> Can you resolve ip's via dns? I.E. ping google.com or can you only ping 192.168.0.254 for example?

Yes, ping will resolve domain names (i.e. google.com). I guess I don't understand how applications get network connection settings, and how that differs from ping.

---

### Post by ronacc on 2009-02-21
have you tried   sudo apt-get update ? if that dosent connect ,reboot into recovery mode and try it .

---

### Post by diafygi on 2009-02-21
> **ronacc said:**
> have you tried   sudo apt-get update ? if that dosent connect ,reboot into recovery mode and try it .

Apt-get update only returns errors, even in recovery mode:
```
Err http://security.ubuntu.com jaunty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done           
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, 
```

Why is ping the only thing that resolve domain names?

---

### Post by ronacc on 2009-02-21
take a look at post #8 in this thread   [http://ubuntuforums.org/showthread.php?t=1062215&highlight=resolv.conf](http://ubuntuforums.org/showthread.php?t=1062215&highlight=resolv.conf)  
 also post your resolc.conf file

---

### Post by diafygi on 2009-02-21
> **ronacc said:**
> take a look at post #8 in this thread   [http://ubuntuforums.org/showthread.php?t=1062215&highlight=resolv.conf](http://ubuntuforums.org/showthread.php?t=1062215&highlight=resolv.conf)  
 also post your resolc.conf file

Ok, here's my route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.169.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.169.1.1     0.0.0.0         UG    0      0        0 wlan0
```

Also, isn't the default gateway for route -n supposed to be 192.169.1.*254*? I tried changing it to 192.169.1.254, but that doesn't work.

And here's /etc/resolv.conf:
```
# Generated by NetworkManager
nameserver 192.168.1.254
```

I noticed how resolv.conf shows the nameserver as 192.*168*.1.254 instead of 192.**169**.1.254 (my router is configured to assign 192.169.1.x). I tried changing the nameserver to 192.169.1.254, but that doesn't help.

In the [thread]("http://ubuntuforums.org/showthread.php?t=1062215") you suggested, the OP wasn't able to ping anything. So, I'm not sure that I have the same problem, since I can ping domains just fine.

EDIT: Also, every time I would restart NetworkManager or reboot, my changed settings would go away and I would be left with the default outputs above.

EDIT2: The host command seems to be working correctly:
```
$host www.google.com
www.google.com is an alias for www.l.google.com.
www.l.google.com has address 64.233.161.99
www.l.google.com has address 64.233.161.147
www.l.google.com has address 64.233.161.104

```

---

### Post by caryb on 2009-02-22
192.169.* is usually a address that is applied when no DHCP server is not found, seems to me that your router is not forwarding DNS requests, to test this change your dns server in resolv.conf to 139.130.4.4 (Australian DNS server) & see if you can resolve eternal address. If it does I would be looking at your routers DNS servers. Once you are connected to the net you can look up what your ISP suggests is your DNS servers.


Cary

---

### Post by ronacc on 2009-02-22
I am about out of things to sugest everything looks fine but you are not connecting except to ping . your route -n is exactly the same as mine , your resolv.conf looks a little strange , I have 192.168.1.1  and 192.168.2.1  (2 routers 1 wired 1 wireless)  you might want to try the address of your router ,  probably one of those .

---

### Post by ronacc on 2009-02-22
try what caryb said first , that will put the routing outside of your box/router .

---

### Post by diafygi on 2009-02-22
> **caryb said:**
> 192.169.* is usually a address that is applied when no DHCP server is not found, seems to me that your router is not forwarding DNS requests, to test this change your dns server in resolv.conf to 139.130.4.4 (Australian DNS server) & see if you can resolve eternal address. If it does I would be looking at your routers DNS servers. Once you are connected to the net you can look up what your ISP suggests is your DNS servers.

Amazing! I changed /etc/resolv.conf from:
```
# Generated by NetworkManager
nameserver 192.168.1.254
```
to:
```
# Generated by NetworkManager
nameserver 139.130.4.4
```
and I can connect to the internet! Woot! Thanks a million.

I will update [Bug #329937]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/329937") with a workaround. However, this is only a temporary fix since any restart of Network Manager or reboot will revert the nameserver back to 192.168.1.254

What's also curious is that 192.68.1.254 works with Intrepid just fine. I wonder what changed with Jaunty. I looked at my router's config (Linsys WRT54GS), and my dsl modem is giving only one DNS address (192.168.1.254, see screenshot).

Also, why did ping work when other programs didn't? Hmmm.

---

### Post by caryb on 2009-02-22
Ok that diagnoses proved that there is issues with your routers DNS, your router acts as a DNS proxy so I would web into your router & see what dns servers it's using. Then go to your isp's website & see what they should be then modify the routers DNS. If that gives no joy change the dns in the router to the 139.130.4.4 (it's a quick underworked DNS server) & see if that works for you after a reboot.


Cary

---

### Post by diafygi on 2009-02-22
> **caryb said:**
> Ok that diagnoses proved that there is issues with your routers DNS, your router acts as a DNS proxy so I would web into your router & see what dns servers it's using. Then go to your isp's website & see what they should be then modify the routers DNS. If that gives no joy change the dns in the router to the 139.130.4.4 (it's a quick underworked DNS server) & see if that works for you after a reboot.

Unfortunately, my router is relying on a dsl modem supplied by my ISP. So, I don't know if I can change the DNS listings for the dsl modem (I'll have to look into this). In my last post, I attached a screenshot of my router config.

I have some questions:
-Why is Intrepid dealing with the 192.168.1.254 DNS address fine?
-Why is ping in Jaunty dealing with the 192.168.1.254 DNS address fine?

---

### Post by ronacc on 2009-02-22
aha the WRT54gs is a strange and wonderous beast , I had one a couple of years ago that caused me to remove large hadfulls of my hair trying to beat it into submission , in the end it won and I replaced it with a cheap airlink101 which has had 0 problem with anything I have thrown at it .

---

### Post by diafygi on 2009-02-22
> **ronacc said:**
> aha the WRT54gs is a strange and wonderous beast , I had one a couple of years ago that caused me to remove large hadfulls of my hair trying to beat it into submission , in the end it won and I replaced it with a cheap airlink101 which has had 0 problem with anything I have thrown at it .

Ha, irony. I replaced my airlinn101 with this wrt54gs because the airlink was constantly dropping connections (to be expected after 2 yrs and cheap equipment).

Anyway, now that I've been able to connect to the internet, I updated all of Jaunty's packages via synaptic. The problem has officially gone away. The default nameserver generated by NetworkManager in /etc/resolv.conf now works:
```
# Generated by NetworkManager
nameserver 192.168.1.254

```

Crazy, huh? Don't know what changed in the updates to allow that to work, but it does. Case closed! Thanks a lot ya'll!

---

