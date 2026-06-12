---
title: "just upgraded to intrepid&amp; now i cant get packages!"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by papasnurf on 2008-11-07
When i tried to use synaptic to download a couple of codecs (that disappeared in the switch from hardy to intrepid) AN ERROR OCCURED.    


 W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-15_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xaw3d/xaw3dg_1.5+E-15_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-15_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/3/3dchess/3dchess_0.8.1-15_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

**i'm a newb. i need help. please.**
(those are not the original packages i tried. it is doing that for ALL of them)

---

### Post by scragar on 2008-11-07
Are you using a proxy or something similar(tor sounds likely)?

Open synaptic, go Settings>preferences, then the network tab and try selecting direct connection. Apply, close, then click reload, and try installing software again.

---

### Post by CrazyMonkey77 on 2008-11-07
If this has occurred just after your upgrade then it could be that your network hasn't installed properly so it's trying to connect to a localhost address. (though I'm not sure why it's trying to connect to that port)

Open a terminal and type "sudo dhclient" to get a new ip address.

then go to "Add remove applications" and install network manager if it's not already installed.  This has been quite a common problem I think recently.

Hopefully this should work, though it could be something different...

---

### Post by papasnurf on 2008-11-07
> **scragar said:**
> Are you using a proxy or something similar(tor sounds likely)?

Open synaptic, go Settings>preferences, then the network tab and try selecting direct connection. Apply, close, then click reload, and try installing software again.
i tried but a direct connection was already selected and when i hit reload it attempted to but then the error reared its ugly head again and i got about 20 of these:
 W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

what exactly is the localhost?

---

### Post by papasnurf on 2008-11-07
.

what exactly is the localhost?[/QUOTE]
that certainly did something but its gunna take me a few to figure out what

---

### Post by CrazyMonkey77 on 2008-11-07
localhost refers to the local loopback interface of your machine.  It's useful for testing as it behaves in the same way as a normal network host but without the need to involve your network card and get out on a network.

If you haven't got a valid IP address, most network dependent programs will try to use your localhost as it's the only valid TCP/IP device they can see, that's why I thought of the IP problem first.

I'd try to see if this has resolved your problem, if it has, then install "network manager" from "add/remove" on the applications menu which will probably fix this in the future

---

### Post by papasnurf on 2008-11-07
i dont know what mostof this code means so i"ll have to post it:

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/0a:e7:70:79:83:7b
Sending on   LPF/pan0/0a:e7:70:79:83:7b
Listening on LPF/wlan0/00:c0:a8:c2:2f:25
Sending on   LPF/wlan0/00:c0:a8:c2:2f:25
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:03:25:3d:54:9a
Sending on   LPF/eth0/00:03:25:3d:54:9a
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.2 from 192.168.2.1
DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.2 from 192.168.2.1
bound to 192.168.2.2 -- renewal in 921430171 seconds.

the good news is that i already have network manager and the really good news is that my wireless connection is working for the first time in a month! i dont know how that worked but thank you CrazyMonkey. but still i cant download packages.

---

### Post by CrazyMonkey77 on 2008-11-07
Oh ok - at least I can see that you're getting a dhcp lease now.  I'd try a couple of other things to see if it's a dns issue.

can you open a terminal and try to ping the host you are trying to connect to to see if it resolves to an the correct IP using the command:

ping archive.canonical.com

type <ctrl> + <c> to stop the ping

On a side note - I've heard that this can be caused by having a certain package installed called anon-proxy.  can you let me know the output of the following command:

sudo dpkg --get-selections | grep anon

---

### Post by papasnurf on 2008-11-07
it says :
anon-proxy					deinstall

what is it?

---

### Post by papasnurf on 2008-11-07
This is the result of the ping

:~$ ping archive.canonical.com
PING archive.canonical.com (91.189.90.142) 56(84) bytes of data.
64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=1 ttl=47 time=135 ms

64 bytes from archive.canonical.com (91.189.90.142): icmp_seq=16 ttl=47 time=132 ms
^C
--- archive.canonical.com ping statistics ---
16 packets transmitted, 16 received, 0% packet loss, time 15062ms
rtt min/avg/max/mdev = 132.504/133.947/135.554/0.885 ms

what does that mean?

---

### Post by CrazyMonkey77 on 2008-11-07
It's a web proxy designed to kind of disguise where you're coming from.  It sounds like it re-routing your httpd traffic.

You can remove it by typing 

sudo apt-get remove anon-proxy

Edit: just seen your ping response and looks like dns is working ok..

---

### Post by papasnurf on 2008-11-07
> **CrazyMonkey77 said:**
> It's a web proxy designed to kind of disguise where you're coming from.  It sounds like it re-routing your httpd traffic.

You can remove it by typing 

sudo apt-get remove anon-proxy

Edit: just seen your ping response and looks like dns is working ok..
that was it. i got anon-proxy off this computer and did a restart(coincidently) and everything is working like its supposed to. thanx for all the help, i really appreciate it. the Ubuntu community is awsome.

---

### Post by CrazyMonkey77 on 2008-11-07
no worries, though I must confess that scragar was slightly more on the ball than me on the initial diagnosis.  We got there in the end :)

---

