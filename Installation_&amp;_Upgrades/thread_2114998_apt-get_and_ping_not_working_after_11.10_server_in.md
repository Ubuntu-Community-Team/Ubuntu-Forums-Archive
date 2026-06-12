---
title: "apt-get and ping not working after 11.10 server install"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by pjizz on 2013-02-11
hello all,

I recently installed Ubuntu Server 11.10 on an old Dell laptop.  I went with 11.10 because the laptop is non-PAE.  My plan is to use the laptop as a cheap media server to sling my media to another box that has xbmc and his hooked up to my tv.

When I installed, at the select software screen, i chose
[LIST]
[*]openssh server
[*]dns server
[*]samba server
[*]LAMP server
[/LIST]

Everything in the install goes fine.  

When I reboot and login, I am unable to use apt-get. 

Concerned, I tried to ping google.com but got an unknown host error.  I was able to ping another machine's IP on my local network.

Any advice on where to go next?  I tried fooling around with /etc/network/interfaces and /etc/resolv.conf using info culled from other people online with similar issues.  but none of this worked.

The machine is hooked to a router with DHCP, and - if I understand this correctly - the router should be giving IP addresses to the machines.  The router is hooked up to a cable modem.  Internet works fine on all the other machines.

thanks!

---

### Post by TheFu on 2013-02-11
Thanks for explaining the reason for 11.10, however, it is out of support. You'd be better served installing 10.04 LTS which will be supported with patches until 2015.

For a server, you do not want DHCP. You want to manually specify the IP or have your router provide a static IP using DHCP MAC address reservations.

If you post your /etc/resolv.conf and /etc/network/interfaces, we might be able to help.
Here's an article about setting up a router to use DHCP for reservations:  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

---

### Post by CharlesA on 2013-02-11
> **TheFu said:**
> Thanks for explaining the reason for 11.10, however, it is out of support. You'd be better served installing 10.04 LTS which will be supported with patches until 2015.

+1.

> For a server, you do not want DHCP. You want to manually specify the IP or have your router provide a static IP using DHCP MAC address reservations.

If you post your /etc/resolv.conf and /etc/network/interfaces, we might be able to help.
Here's an article about setting up a router to use DHCP for reservations:  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

Agreed. I have my production server set to use a static IP, but my test server is set to user DHCP reservation (which all the clients on my home network use).

Posting /etc/network/interfaces might help too.

---

### Post by sanderj on 2013-02-11
A DNS issue? Try this:

```
host www.google.com
host www.google.com 8.8.8.8
mtr -nrc2 8.8.8.8
```

and post the output here

---

### Post by pjizz on 2013-02-11
> **TheFu said:**
> If you post your /etc/resolv.conf and /etc/network/interfaces, we might be able to help.
Here's an article about setting up a router to use DHCP for reservations:  [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

/etc/resolv.conf is as follows
```
domain hsd1.tn.comcast.net
search hsd1.tn.comcast.net
nameserver 10.0.0.1
```

for what it's worth, 10.0.0.1 does represent my router IP.

/etc/network/interfaces is as follows
```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```


> **sanderj said:**
> A DNS issue? Try this:

```
host www.google.com
host www.google.com 8.8.8.8
mtr -nrc2 8.8.8.8
```

and post the output here

output of the above is as follows

```
parker@d600server:~$ host www.google.com
;; connection timed out; no servers could be reached
$ host www.google.com 8.8.8.8
;; connection timed out; no servers could be reached
$ mtr -nrc2 8.8.8.8
HOST: d600server Loss% Snt Last Avg Best Wrst StDev
```

on that last mtr command, I'm assuming there were supposed to be values under each of those columns.  There were none.

> **TheFu said:**
> Thanks for explaining the reason for 11.10, however, it is out of support. You'd be better served installing 10.04 LTS which will be supported with patches until 2015.

For a server, you do not want DHCP. You want to manually specify the IP or have your router provide a static IP using DHCP MAC address reservations.

I am familiar with using my router's DHCP reservation to reserve IP addresses for certain machines.  I've done this to make it easier to mount network shares.  You say "specify the IP **or** have your router provide a static IP using DHCP MAC address reservations"...what would the /etc/network/interfaces look like if I did that second option.

THANKS so much for all of the quick help.  This is the reason I stick with Ubuntu, through thick and thin (or gnome2 and unity) ;)

In the meantime, I am downloading Ubuntu Server 10.04

---

### Post by TheFu on 2013-02-11
Ok, so your router is providing DNS?  Are you absolutely positive that is working?

In the meantime, add (do not replace) **ADD these lines **to the bottom of the /etc/resolv.conf.
```

nameserver 208.67.222.222
nameserver 208.67.220.220
```These are primary and 2ndary name servers for open DNS in the USA.
You can, and should, probably have 3 DNS providers.

You can use any other DNS provider you like, of course.

After a few minutes tops, the new DNS should be used.  Verify that you can reach them with a 
[B]ping 208.67.222.222

man interfaces [/B]will explain the config for that fileso you can have static IPs. If you are going to run a server, learning about man pages is critical. The basic options are address, gateway, netmask ...

---

### Post by pjizz on 2013-02-11
I have OpenDNS setup on my router.  Doesn't that mean I shouldn't need to worry about nameservers at the machine level.  All of my computers use OpenDNS this way.

---

### Post by pjizz on 2013-02-11
also, I'm not saying that I think the nameserver line defining 10.0.0.1 (my router) as a nameserver SHOULD be there, I'm just saying that it is.  Clearly something is not working.  What I do know is that all of my other computers are able to resolve DNS just fine on the same network, same router

---

### Post by CharlesA on 2013-02-11
> **pjizz said:**
> I have OpenDNS setup on my router.  Doesn't that mean I shouldn't need to worry about nameservers at the machine level.  All of my computers use OpenDNS this way.

You still need to tell the machine where it needs to look to DNS information.

> **pjizz said:**
> also, I'm not saying that I think the nameserver line defining 10.0.0.1 (my router) as a nameserver SHOULD be there, I'm just saying that it is.  Clearly something is not working.  What I do know is that all of my other computers are able to resolve DNS just fine on the same network, same router

If you cannot ping by IP, then something is wrong with the setup of that specific machine.

---

### Post by TheFu on 2013-02-11
> **pjizz said:**
> also, I'm not saying that I think the nameserver line defining 10.0.0.1 (my router) as a nameserver SHOULD be there, I'm just saying that it is.  Clearly something is not working.  What I do know is that all of my other computers are able to resolve DNS just fine on the same network, same router

That is correct and probably just fine, but something isn't working. 
Please describe every part of your networking and post the **ifconfig **and **route **output.

If you can't ping 8.8.8.8 or those NS IPs that I provided before, then your Linux box isn't getting on the internet.  That means either there is a physical issue or something isn't configured correctly.  It could be as simple as the wrong dhcp server is being found and providing the wrong netmask.

How good are you at networking? Good understanding of IPv4?

---

### Post by MAFoElffen on 2013-02-12
> **CharlesA said:**
> You still need to tell the machine where it needs to look to DNS information.

If you cannot ping by IP, then something is wrong with the setup of that specific machine.
A little different perspective... just something that I see from the outside of this.

Review, 11.10 server, other pc's on network, cable modem... 

Is there any router, hub or switch connecting from the modem, then to the other pc's? Just to get an idea of how this is physically laid out. So if so with something else there, then the server is 2 deep from the modem?

What is the IP of the cable modem? Is the cable modem handling dhcp? Is the cable modem also the gateway, so same IP address? 

No IPp address for gateway specified in /etc/networking/interfaces so it should be dynamic, but sometimes in 11.10 server if would get confused... Especially if the gateway is not in the cable modem, but somewhere else on the newtowrk. At least in two of 10 of my servers, when they were back on that version, had this problem. They were confused.

Second, backup the resolve conf file and just add those IP's of to the outside open dns servers posted above... to temporarily take that out of the picture to test and outside connection.

Because? Well, immaterial of static ip, dhcp or whatever... he can ping a PC on his network by ip from that server, right? Can he ping that server IP from that PC? One way would say firewall running somewhere? 

So physically, if he can ping back and forth within the network, basic networking function are working. That leaves gateway and dns, right?

Is the handshake to the ISP in the cable modem or in a router on the home network side of that?

Can he ping the cable modem by IP? If the gateway is in the cable modem, can he bring up the html page of the cable modem and see what IP's it says for the ISP host and their DNS servers? (On a browser from any PC on the network.)

If he can do all that, then it's either a gateway problem or dns...

If he can ping anything in these ranges:
```

64.233.160.0 - 64.233.191.255
66.102.0.0 - 66.102.15.255
66.249.64.0 - 66.249.95.255
72.14.192.0 - 72.14.255.255
74.125.0.0 - 74.125.255.255
209.85.128.0 - 209.85.255.255
216.239.32.0 - 216.239.63.255

```
Those are the IP addresses for [www.google.com](www.google.com) servers. Specifically ping one of the addresses in those ranges... and that would bypass DNS, right?

You're right in that it's something on that server. Blank/not specified should pass the dynamically passed value from a router or gateway to the system... But's it's not getting there. So either he over-specified it in those two files (and got one or more of them wrong) or he needs help it along it's way if it is "confused" by specifying something that exists there.

Making sense?

---

### Post by CharlesA on 2013-02-12
Nice write up, MAFoElffen. :)

When I am troubleshooting network problems I usually follow this method:

Ping localhost
Ping gateway (router) via ip address
Ping another host on the same network segment by hostname and ip address
Ping a known website (google.com, ubuntu.com, fedoraproject.org, etc) by FQDN.

If any step fails, I will know where to start looking.

---

### Post by sanderj on 2013-02-12
(TL;DR)

What's the output of:

```
ip route show
```

---

### Post by TheFu on 2013-02-12
> **CharlesA said:**
> Nice write up, MAFoElffen. :)

When I am troubleshooting network problems I usually follow this method:

Ping localhost
Ping gateway (router) via ip address
Ping another host on the same network segment by hostname and ip address
Ping a known website (google.com, ubuntu.com, fedoraproject.org, etc) by FQDN.

If any step fails, I will know where to start looking.

+1 - that is an excellent order to determine where the issue lies, CharlesA. Nice. No extra steps unless wifi is used.

If you can't ping IPs on the internet, then you will have a DNS issue. THAT is certain.  Without a gateway + netmask specified, I think the routing is screwed for anything external.

The  router required by Comcast for my business-class service provides a 10.x.x.x address range to my internal devices. On business class, if you have multiple public IPs, you can ignore the 10.x.x.x space and tell YOUR router to use the public IPs assigned. The Comcast router is the gateway for the subnet, but only my router knows that. For all internal devices, my router is the gateway.  I share this just to point out that there are many different home routing configurations.  OTOH, if you are a business class customer, there is a good help-line to get this all worked out.

We should also point out that server networking changed a little with the 12.04 release.  We no longer directly modify the /etc/resolv.conf anymore. DNS servers must be configured in the "interfaces" file. This is an important understanding to anyone lurking.  The file, resolve.conf, that has been used to specify DNS servers for 20+ yrs is not used by humans anymore since 12.04 (and I suspect all the other distros switched around that same time too).

---

### Post by pjizz on 2013-02-12
> **TheFu said:**
> If you can't ping 8.8.8.8 or those NS IPs that I provided before, then your Linux box isn't getting on the internet.  That means either there is a physical issue or something isn't configured correctly.  It could be as simple as the wrong dhcp server is being found and providing the wrong netmask.

How good are you at networking? Good understanding of IPv4?

My experience with networking is as follows: [LIST]
[*]I've used nautilus to access smb and sftp shares
[*]i've mounted network folders via openssh
[*]i've been **somewhat** successful at automounting ssh shares at boot[/LIST]

So I guess you could say I'm just above novice.

Anyhow, I continued to tinker last night.  I tried to switch the /etc/network/interfaces to a static IP and used the values that my router's web interface listed.  I also tried to copy the /etc/resolv.conf and the /etc/network/interfaces of other machines on the network.  Neither of those options worked.

I'm not wanting to give up, because I consider increasing my Linux proficiency to be an ongoing hobby, but while I'm at it, I'm wondering if my approach is even necessary.

What I want is a multi-box system, with one box playing network media via XBMC on a tv, another box working as my desktop and terminal for administering things, and a third box hosting the media and doing the grunt work of torrenting, TEDing, couchpotating, etc.  

I came up with this plan after deciding that my current system - two boxes, with one being both my desktop computer AND doing all the grunt work - was not good.  Things were slow, and I decided it was because my desktop couldn't handle running an X GUI while also processing all of the files.  Maybe that was a wrong assumption.

I then assumed that I should setup a server to house the media and process it all with deluge, couchpotato, etc.  I'm wondering if maybe that was a bad assumption.

For what I want, would you all suggest any different configuration?  Maybe I could make things run more smoothly by installing a minimal ubuntu system (using the mini.iso) on the media playing computer, and then still letting the desktop do everything else.  What do you guys suggest?

Thanks still for all the help

---

### Post by CharlesA on 2013-02-12
What does your interfaces file look like now?

Also try running **ip route show** as sanderj suggested.

---

### Post by TheFu on 2013-02-12
Not to be rude, but your description makes me think you are a networking neophyte. 
We all were at some point.  Small networking is much easier to learn than Linux, IMHO.  Nobody knows what they don't know.  Networking can be extremely complex as I've learned working in telecom/ISPs.  Some of their network designs make my head spin.

For example, is 10.0.0.1/24 the same as 10.0.0.0/255.255.255.0 when describing a network?  
How many useable IP addresses are provided in that example network?  
Is a router necessary for the machines inside the subnet to communicate?
There are IPv4 primers that should teach this in an hour or 2.  Having a simplified understanding of networking for a home environment will repay the effort every year for the rest of your life.

To learn more, go here: [https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm) and listen/read to episodes 25-29 - there is a bunch of excess talking, but the hosts do a good job of explaining how things fit together.

I don't know what PC the normal workload is, but I would expect a Core2Duo or better could easily handle all that if the processes were properly prioritized and not starved for RAM.  Check out the **nice **command.  Put your low priority tasks at a lower nice level and only leave time specific tasks at normal priority.  Downloading stuff should be the lowest priority.  Prioritization is key.

Batch processing during non-busy periods is also a technique you probably haven't mastered.  If you do any transcoding, limiting the number of tasks at any 1 time will get more of them completed over the same period.  Swapping between too many tasks can slow down a PC.  I use **task-spooler** to manage batch queues.  Anything run batch should be low priority.

X/Windows is a hog.  I don't load it on "servers" at all. It sucks resources that are better used for disk buffers.  Still, I LOVE X/Windows - it lets me open and manage many more terminal sessions!

If you are interested in seeing what others are doing with their home networks, check out [http://www.ratemynetworkdiagram.com/index2.php](http://www.ratemynetworkdiagram.com/index2.php) to see lots of network diagrams.  I like this one: [http://www.ratemynetworkdiagram.com/?i=15442](http://www.ratemynetworkdiagram.com/?i=15442)  Complicated, but with some different security zones for different classes of devices.

---

### Post by MAFoElffen on 2013-02-13
> **TheFu said:**
> <<Edited>>
Wow. I guess you don't work in customer service or sales. LOL

I was going to say something to fuel the flames on server graphics, but that doesn't help the OP with his problem.

So- Meanwhile, back at the ranch... (Back on subject)

I are here to help users. This OP in particular has a networking problem on a server install. He has 11.10 installed and has "networking" working, but no path to the outside world from that box.

11.10 used interfaces and resolve.conf (even though 12.04 changed that later).

The OP, in process, changed interfaces to static.

So- Info still? 
- What is the new ip of server.
- What is IP of cable modem/gateway?
- Did he add the gateway IP to interfaces?
- Did he take out the IP of his local DNS server to test if it could receive dynamically? 
-Or to use the OpenDNS Server IP's?:
```

208.67.222.222
208.67.220.220
208.67.222.220
208.67.220.222

```

---

### Post by CharlesA on 2013-02-13
> **MAFoElffen said:**
> 11.10 used interfaces and resolve.conf (even though 12.04 changed that later).

The OP, in process, changed interfaces to static.

The only difference that I can see with networking between 11.10 and 12.04 is the inclusion of a dynamically generated resolv.conf.

The setup for a static IP is the same in the interfaces file, but you will need to add dns-nameservers and dns-search included in addition to all the other stuff.

I found some good examples over on the [Debian wiki]("http://wiki.debian.org/NetworkConfiguration").

As of now, we don't really have much to go on as the OP hasn't replied back to any of the information we have asked for.

---

### Post by pjizz on 2013-02-16
Thanks for all the help.  Was too busy prepping for a lecture on the Scientific Revolution, but still want to keep soldiering, in the tradition of Galileo et al.

> **TheFu said:**
> Please describe every part of your networking and post the **ifconfig **and **route **output.

I'm assuming you meant describe the physical layout, as other have queried?

I have cable running from the pole outside on the curb to my house :)

That goes into the wall, and from there into a cable modem.  Motorola SB 5120.  Cat5 goes from that to a router, D-LINK DIR-615.  Cat5 then goes from the router to three computers: two desktops that connect to the internet just fine, both running Ubuntu 12.10, and this one laptop, running Ubuntu Server 11.10, which is having the internet issues.

The IP for my router is 10.0.0.1.  The router's subnet mask is 255.255.255.0  (I got both those number from the router's web interface)

I assign IP to attached machines via the router's DHCP, range 10.0.0.200 to 10.0.0.254

the output for ~$ route:

```
Kernel IP routing table
Destination   Gateway   Genmask       Flags Metric Ref Use Iface
default       10.0.0.1  0.0.0.0       UG    100    0     0 eth0
10.0.0.0      *         255.255.255.0 U     0      0     0 eth0
10.0.0.0      *         255.255.248.0 U     0      0     0 eth0
```

the output for ~$ ifconfig:
```

eth0  Link encap:Ethernet HWaddr 00:0f:1f:a7:82:d9
      inet addr:10.0.0.207 Bcast:0.0.0.0 Mask:255.255.248.0
      inet6 addr: fe80::20f:1fff:fea7:82d0/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:208 errors:0 dropped:0 overruns:0 frame:0
      TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:31614 (31.6 kb) TX bytes:22030 (22.0 KB)
      Interrupt:11

lo    Link encap:Local loopback
      inet addr:127.0.0.1 Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING MTU:16436 Metric:1
      RX packets:54 errors:0 dropped:0 overruns:0 frame:0
      TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:4508 (4.5 KB) TX bytes:4508 4.5 KB)

```

the output for ~$ ip route show is
```
default via 10.0.0.1 dev eth0 metric 100
10.0.0.0/24 dev eth0 proto kernel scope link src 10.0.0.207
10.0.0.0/21 dev eth0 proto kernel scope link src 10.0.0.207
```

---

### Post by pjizz on 2013-02-16
> **CharlesA said:**
> Nice write up, MAFoElffen. :)

When I am troubleshooting network problems I usually follow this method:

Ping localhost
Ping gateway (router) via ip address
Ping another host on the same network segment by hostname and ip address
Ping a known website (google.com, ubuntu.com, fedoraproject.org, etc) by FQDN.

If any step fails, I will know where to start looking.

ping localhost                 = 0% packet loss
ping router at 10.0.0.1        = 100% packet loss
ping network box at 10.0.0.200 = 0% packet loss
ping same box at inspiron530   = unknown host inspiron530
ping a ubuntu.com              = 100% packet loss

fwiw, the host named inspiron530, ip address 10.0.0.200 **can** ping the server via hostname

---

### Post by CharlesA on 2013-02-16
> **pjizz said:**
> 
the output for ~$ ifconfig:
```

eth0  Link encap:Ethernet HWaddr 00:0f:1f:a7:82:d9
      inet addr:10.0.0.207 [COLOR="Red"]Bcast:0.0.0.0[/COLOR] [COLOR="RoyalBlue"]Mask:255.255.248.0[/COLOR]
      inet6 addr: fe80::20f:1fff:fea7:82d0/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:208 errors:0 dropped:0 overruns:0 frame:0
      TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:31614 (31.6 kb) TX bytes:22030 (22.0 KB)
      Interrupt:11

```


Your network config of that box is all screwy. What does your /etc/network/interfaces file look like?

ifconfig should look something like this:
```
eth0      Link encap:Ethernet  HWaddr 50:e5:49:5b:f5:37
          inet addr:192.168.1.2  [COLOR="Red"]Bcast:192.168.1.255[/COLOR]  [COLOR="Blue"]Mask:255.255.255.0[/COLOR]
          inet6 addr: fe80::52e5:49ff:fe5b:f537/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:250729417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270447959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:214860574611 (214.8 GB)  TX bytes:339786921761 (339.7 GB)
          Interrupt:44 Base address:0xe000

```

Here is what my interfaces file looks like:

```
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search local
        dns-nameservers 192.168.1.1

```

---

### Post by TheFu on 2013-02-16
It looks to me like you have the netmask specified in 2 places AND those specs are different.  You probably (almost certainly) only want a 255.255.255.0 netmask.  That should remove the route that says 10.0.0.0/21.  That looks funny to me.

A simple route (which is what you really want):
```
$  ip route show
default via 192.168.1.1 dev eth0  metric 100 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.11 
```
Clearly, all the 192.168.x.x needs to be translated to 10.x.x.x for your subnet. 

You do not want 2 interfaces on the same subnet unless you really know what you are doing.

---

### Post by pjizz on 2013-02-17
So I decided to try from scratch, reinstall.  Booting with a 11.04 server disc, the install fails to autoconfigure DHCP, just like it did last time I installed.  Last time, I just went ahead with the install without automatically configuring network.  This time I tried the "manually configure network" option, using the numbers I think should work, 10.0.0.207 for IP address, 10.0.0.1 for router, 255.255.255.0 for subnet mask...

we shall see

---

### Post by TheFu on 2013-02-17
For a server, you should really be installing either 10.04 or 12.04 releases. These will be more stable than others and get supported/patches for 5 yrs.  11.04 is out of support.

That IP and subnet seem fine.  I think the comcast router is at 10.0.0.1 too, but I can't get to it right now - the networking here is a little more complex than most homes. That is reasonable for the gatway of your internal machines.

The machines that work will have all the network settings that you need to know.  Only the IP address would be different.  On MS-Windows, the **ipconfig /all** command will display what you need to know.  I would suggest that if you do use static IPs, then you want those to be outside the range that a DHCP server would assign.

---

### Post by pjizz on 2013-02-17
> **TheFu said:**
> For a server, you should really be installing either 10.04 or 12.04 releases. These will be more stable than others and get supported/patches for 5 yrs.  11.04 is out of support.

The machines that work will have all the network settings that you need to know.  Only the IP address would be different.  On MS-Windows, the **ipconfig /all** command will display what you need to know.  I would suggest that if you do use static IPs, then you want those to be outside the range that a DHCP server would assign.

I will try to install 10.04 this evening.  I still think that the root problem is the installer failing to autoconfigure the networking with DHCP.  I've tried proceeding without configuring the network and then editing the interfaces file, and I've tried to manually configure the network via the installer.  Neither of this approaches worked.

I also had your reaction "the machines that work willhave all the network settings that you need to know."  Weirdly enough, my /etc/network/interfaces file on my main desktop only has the loopback interface enabled.  There is nothing for the eth0 in the file.  It works fine, internet and LAN.  Googling and searching the forums for people who's install fails at configuring the network only tells me that other people have had this problem, but I haven't found a solution that works for me.

I know that my router serves as a DHCP server, because I can successfully manipulate the IP address of machines on the network.  Why it won't work on this machine is killing me

---

### Post by jdthood on 2013-02-17
> **pjizz said:**
> Weirdly enough, my /etc/network/interfaces file on my main desktop only has the loopback interface enabled.  There is nothing for the eth0 in the file.

Presumably your main desktop is running NetworkManager.

---

### Post by CharlesA on 2013-02-17
> **jdthood said:**
> Presumably your main desktop is running NetworkManager.

Likely.

A server /etc/network/interfaces file should look like the one I posted above.

As far as having the machine unable to grab an address from DHCP, are you sure there isn't a problem with it communicating with the DHCP server (likely 10.0.0.1)?

---

### Post by pjizz on 2013-02-17
> **CharlesA said:**
> Likely.

As far as having the machine unable to grab an address from DHCP, are you sure there isn't a problem with it communicating with the DHCP server (likely 10.0.0.1)?

seems likely, especially since I cannot ping 10.0.0.1 via that machine, whereas I can ping the localhost and I can ping other boxes on the network.  but I am at a loss as for how to solve that issue

---

### Post by sanderj on 2013-02-17
> **pjizz said:**
> seems likely, especially since I cannot ping 10.0.0.1 via that machine, whereas I can ping the localhost and I can ping other boxes on the network.  but I am at a loss as for how to solve that issue

Is this a home network, or work?

The other machines: which default gateway do they use? 10.0.0.1 or something else?

---

### Post by pjizz on 2013-02-17
> **sanderj said:**
> Is this a home network, or work?

The other machines: which default gateway do they use? 10.0.0.1 or something else?

home network, just three machines connected to a router.  the others use 10.0.0.1 as the gateway

---

### Post by CharlesA on 2013-02-17
Boot a livecd on that machine and see if you can ping the gateway. That will help tell if it is a problem with the OS or a problem with the hardware.

---

### Post by TheFu on 2013-02-17
> **pjizz said:**
> home network, just three machines connected to a router.  the others use 10.0.0.1 as the gateway

Ubuntu Server and Ubuntu Desktops use different methods to manage network setup. For a server there are two ways, both happen in the /etc/network/interfaces file.

* DHCP
* Static IP
In a simple configuration, do not tell the same device to use both DHCP and static IP.  One or the other.

Being able to access other machines on the network works because the netmask is either correct or not screwed enough to matter.  Not being able to ping the router ... well, that could mean that the gateway is incorrectly specified OR the netmask is hooky.

Look at the interfaces file that oldfred put above and use **man interfaces** to convert it for your network.

---

### Post by CharlesA on 2013-02-18
> **TheFu said:**
> Look at the interfaces file that oldfred put above and use **man interfaces** to convert it for your network.

Not oldfred. :p

But yeah +1. ;)

It should look something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.0.207
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search local
        dns-nameservers 10.0.0.1

```

---

### Post by pjizz on 2013-02-18
> **TheFu said:**
> Ubuntu Server and Ubuntu Desktops use different methods to manage network setup. For a server there are two ways, both happen in the /etc/network/interfaces file.

* DHCP
* Static IP
In a simple configuration, do not tell the same device to use both DHCP and static IP.  One or the other.

One confusion I still have is concerning this.  Should I try to setup a static or dhcp setup for networking?  

I **think** that should be an easy question, since I know I don't have a static IP address from my ISP, but the fact that I can give a static IP address to my computers using DHCP reservation from my router, I don't know what to tell the interfaces file to do.  

Now, I think I know how to set it up either way, but it doesn't seem to be working.  Right now, my interfaces file is simple
```
auto eth0 
iface eth0 inet dhcp
```
but that doesn't seem to be working.  

i like the id of booting with a Live CD and doing the pings.  thanks for that new suggestion.  

if I can isolate the problem to the OS configuration, maybe due to a bad install, how can I avoid the problem with a new install. I've reinstalled multiple versions of ubuntu server, all to no avail.  do I need dhclient running on the server in order to obtain dhcp from the router?

thanks for the continuing support

---

### Post by CharlesA on 2013-02-18
> **pjizz said:**
> rfaces file to do.  

Now, I think I know how to set it up either way, but it doesn't seem to be working.  Right now, my interfaces file is simple
```
auto eth0 
iface eth0 inet dhcp
```
but that doesn't seem to be working.  

Run this and see what it tells you:

```
sudo dhclient
```

> i like the id of booting with a Live CD and doing the pings.  thanks for that new suggestion.  

if I can isolate the problem to the OS configuration, maybe due to a bad install, how can I avoid the problem with a new install. I've reinstalled multiple versions of ubuntu server, all to no avail.  do I need dhclient running on the server in order to obtain dhcp from the router?

thanks for the continuing support

The interfaces file I posted in post 34 gives you a static IP of 10.0.0.207.

---

### Post by jdthood on 2013-02-19
> **pjizz said:**
> 
What I want is a multi-box system, with one box playing network media via XBMC on a tv, another box working as my desktop and terminal for administering things, and a third box hosting the media and doing the grunt work of torrenting, TEDing, couchpotating, etc.

For hosting the content, you could consider buying a NAS off the shelf, e.g., from Synology or NETGEAR.

What hardware do you have running XBMC?

---

### Post by jdthood on 2013-02-19
> **CharlesA said:**
> 
/etc/network/interfaces...
```

        network 10.0.0.0

```

Note that the "network" option is no longer needed, and no longer documented in interfaces(5).

---

### Post by jdthood on 2013-02-19
> **CharlesA said:**
> 
It should look something like this:

```

...
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search local
        dns-nameservers 10.0.0.1
...

```

1. This is not quite right. He's running Ubuntu 11.10 which doesn't have resolvconf installed, so dns-* options in /etc/network/interfaces will have no effect on his system. On Ubuntu 11.10 (but not on Ubuntu 12.04 or later) he should edit /etc/resolv.conf directly so that it contains the following.

```

    nameserver <address>
    search <domain-name-list>

```

2. pjizz, if you can't ping the router by address then the problem is not name service but either hardware or firewall. Perhaps your router has a firewall that excludes traffic from unknown MAC addresses; then you'd have to add the machine's MAC address to the list of known MAC addresses via the router's configuration interface. Or perhaps the router excludes traffic from hosts that are not DHCP clients of the router, and the machine in question is failing to complete DHCP negotiation properly for some reason.

3. By the way, pjizz, why not install Ubuntu 12.04 or 12.10 instead of 11.10?

4. pjizz, another thing. Try to configure your router so that the LAN's TLD (top-level domain) is something other than 'local'. The 'local' TLD is used by mDNS/Bonjour for the domain names of hosts found by mDNS. If you have mDNS enabled on a machine (implemented by the avahi daemon on Ubuntu) then it can interfere with resolving names like 'foo.local' via DNS. Use something like '.private' instead.

---

### Post by jdthood on 2013-02-19
> **pjizz said:**
> One confusion I still have is concerning this.  Should I try to setup a static or dhcp setup for networking?

As DHCP configuration works fine on the other machines you should use DHCP on the machine in question too.

If you want to give a machine a static IP address then might be OK too, but make sure that you configure the router such that it reserves that IP address for the machine in question.

> I **think** that should be an easy question, since I know I don't have a static IP address from my ISP

That just means that the router's WAN address can change. LAN addresses, including the address of the router's LAN interface, are another matter.

> 
Right now, my interfaces file is simple
```
auto eth0 
iface eth0 inet dhcp
```
but that doesn't seem to be working.  


Well, it should work if DHCP works on the other machines on your LAN. Hmm.

> do I need dhclient running on the server in order to obtain dhcp from the router?


Yes. Note that when you configure an interface with "ifup eth0" and you have "iface eth0 inet dhcp" in /e/n/i, ifup runs dhclient for you.

---

### Post by CharlesA on 2013-02-19
> **jdthood said:**
> Note that the "network" option is no longer needed, and no longer documented in interfaces(5).

Really? I guess I never bothered to check because I've been using the same basic interfaces file since 10.04.

> **jdthood said:**
> 1. This is not quite right. He's running Ubuntu 11.10 which doesn't have resolvconf installed, so dns-* options in /etc/network/interfaces will have no effect on his system. On Ubuntu 11.10 (but not on Ubuntu 12.04 or later) he should edit /etc/resolv.conf directly so that it contains the following.

```

    nameserver <address>
    search <domain-name-list>

```


+1. It might be a good idea to install either 10.04 or 12.04 as support for 11.10 ends in April of this year. No support = no updates and that can be a big problem.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by MAFoElffen on 2013-02-20
You know, we assumed if all went well with the install and all was good physical connection and hardware wise, that with all the posted info, this OP should be up by now. What if we assumed wrong?

The OP said this is on an old Dell laptop. He didn't say which specific model. I know on some older Dell and HP's, they used broadcom gigabit and broadcom netextreme nics. They required TG3 firmware, which is non-free non-opensource, so is not on the install disks. It is in linux-firnware-nonfree.deb. 

On different versions of Ubuntu Server install, they would do different things. On the older versions of the install, it would just say that it couldn't bring up dhcp, try manually settings. On other's it would continue on manual settings, but have problems later. On some, you wouldn't know anything from the installer until you installed and rebooted. 

On some, it would continue (no user prompts or messages), substituting a different driver, noting in the logs that it was bringing up the nic card with "limited functionality." this limited functionality never seemed to be quite enough.

Server installs from tty1 and the log displays in tty4. You can review anything still left in the frame buffer using <shift><pageup> and <shift><pagedown>. Pop over to tty4 on Install's first hardware probe...

On some of the newer install disks, it would bring up a dialog saying it was missing firmware. I keep a USB thumbdrive with linux-firmware.deb and linux-firmware-nonfree.deb copied in the root of the thumbdrive. Has covered me for a lot of server hardware besides just those NIC's. I leave it in the USB port until it hits the time server dialog. At the point it is past the hardware probe and the if needed firmware install.

Another not confirmed yet is the physical cabling. It's a laptop. Maybe carry it to a confirmed working wiring and plug in?

Another would be to use a PCMCIA card or USB NIC and see if it auto-connects on plug-in. I've got a few old Dell laptop "docks" here that had wired eth and expansion port slots... Sorry. My spare part bin here is something you'd have to see to believe.

We already also suspect, that since it might not have brought that nic up susccessfully during the install, that there may be something wrong with the install itself, right?

One more curious thing... He installed DNS services on this server and is not configured yet... Never done my own DNS myself, but wondering if anything from that package install could be affecting how it sees or doesn't see things from it's own perspective. I wouldn't think so logically, but then again, it is having problems seeing out.

Like I said, I was just trying to think what else this might be, to make sure all was covered... Otherwise, it looks like we have hit a wall and are discussing the same things over and over again. Right?

---

### Post by CharlesA on 2013-02-20
MAFoElffen: That would make sense, but they can ping other hosts except the gateway, so I don't think it's a physical problem with the switch/cable.

However, it doesn't hurt to rule it out by using a known good cable or switch.

---

### Post by MAFoElffen on 2013-02-20
> **CharlesA said:**
> MAFoElffen: That would make sense, but they can ping other hosts except the gateway, so I don't think it's a physical problem with the switch/cable.

However, it doesn't hurt to rule it out by using a known good cable or switch.

Yes. Pinging to other PC's but not to the router that is goes through to get to those PC's... That's what is really throwing a wrench in this. That is just not "logical." (LOL/bewildered)

Because "that" is not logical, If it were me, at this point, I would not "assume" anything.

Something we can assume. Since the router is handling OpenDNS, dhcp and is the gateway... It is a router, not a switch. The router the OP mentioned is wirelss N with 4 wired ports and an internal port (gateway, usually wired to the modem). I wonder if the laptop has wireless(?)...

One more thing- IP conflict. Net modems and routers both usually come new configured with 10.0.0.1 or 192.168.1.1 as their IP.

I think you (CharlesA) mentioned something about the modem and router having the same IP address... A while back, I had a 3 day wild/frustrating chase tracking this down as a problem. Some said this was okay... different subnets. I can confirm it's not. Some pc's on the net were okay with it... Mostly WIN machines using named services, except their new Ubuntu server... Made each address unique (modem and router/different IP's) and away it went again/ back going again fine.

---

### Post by CharlesA on 2013-02-20
> **MAFoElffen said:**
> I think you (CharlesA) mentioned something about the modem and router having the same IP address... A while back, I had a 3 day wild/frustrating chase tracking this down as a problem. Some said this was okay. I can confirm it's not. Some pc's on the net were okay with it... Mostly WIN machines using named services, except their new Ubuntu server... Made each address unique (modem and router/different IP's) and away it went again/ back going again fine.

I don't really remember, but it get screwy to say the least. I've had to deal with dupliate IP addresses at work and it's not fun, especially when the server that is running DHCP and DNS aren't playing nicely with each other.

I checked my modem and router here (two separate devices) and the router is on 192.168.1.1 and the modem is at 192.168.100.1.

---

### Post by pjizz on 2013-02-23
> **jdthood said:**
> 2. pjizz, if you can't ping the router by address then the problem is not name service but either hardware or firewall. Perhaps your router has a firewall that excludes traffic from unknown MAC addresses; then you'd have to add the machine's MAC address to the list of known MAC addresses via the router's configuration interface. 


***_DING DING DING WINNER WINNER:D:o:):P;):popcorn::KS_***

Thank you SOO much!  I was really getting discouraged until you mentioned that, in that exact way.  I turned on MAC address filtering via the router probably a year and a half ago...really just to see what it did.  I completely forgot about it.  Plug the new machine's HW addr into the router and presto, everything is up and running.  

> **jdthood said:**
> 3. By the way, pjizz, why not install Ubuntu 12.04 or 12.10 instead of 11.10?

the machine in question is non-pae

> **jdthood said:**
> 4. pjizz, another thing. Try to configure your router so that the LAN's TLD (top-level domain) is something other than 'local'. The 'local' TLD is used by mDNS/Bonjour for the domain names of hosts found by mDNS. If you have mDNS enabled on a machine (implemented by the avahi daemon on Ubuntu) then it can interfere with resolving names like 'foo.local' via DNS. Use something like '.private' instead.

I'm not sure how to go about this...is it something I should place on my priority list of things to learn/do?

but again

THANK YOU SO MUCH!  To jdthood and everyone else for your patience and time explaining things to me.  I learned alot in the process.

to do: mark as solved

---

### Post by CharlesA on 2013-02-23
Wow, I thought that MAC address filtering was only for the wireless aspect, but I am glad you got it sorted out. :)

---

### Post by pjizz on 2013-02-23
ya know, I would have said the same thing if I had thought of that earlier, but yea, apparently that was the issue.  now on to configuring this thing.  i'm sure when I've got it all set up, I'll see that my old pc is hardly capable of doing everything i want it to.

---

### Post by TheFu on 2013-02-23
> **pjizz said:**
> ya know, I would have said the same thing if I had thought of that earlier, but yea, apparently that was the issue.  now on to configuring this thing.  i'm sure when I've got it all set up, I'll see that my old pc is hardly capable of doing everything i want it to.

We've all shot ourselves in the foot (and head sometimes) with stuff just like this that we forgot or didn't understand.

For the record, MAC filtering keeps honest people honest. It does not prevent anyone with a tiny bit of knowledge off either wifi or wired ethernet networks. It is like closing a door behind a bush, but not locking it.

---

### Post by CharlesA on 2013-02-23
> **TheFu said:**
> 
For the record, MAC filtering keeps honest people honest. It does not prevent anyone with a tiny bit of knowledge off either wifi or wired ethernet networks. It is like closing a door behind a bush, but not locking it.

+1. It is also fairly easy to get around MAC filtering too, which is why I don't bother using it. I just use a super strong WPA2 key.

---

