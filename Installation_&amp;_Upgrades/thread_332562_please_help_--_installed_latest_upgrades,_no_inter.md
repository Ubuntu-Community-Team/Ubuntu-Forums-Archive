---
title: "please help -- installed latest upgrades, no internet connection now"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by kellopoika on 2007-01-06
Happy Saturday to all . . . I just downloaded and installed the latest upgrades to Dapper Drake and after doing so I've lost my internet connection (I write this from another, non-Linux machine here at home -- so I know it's not a problem with my ISP). Any suggestions? 

Many thanks,

Grant White

---

### Post by louieb on 2007-01-06
DSL? Dial up? 
I just ran  the update also. Had to restart did you?
Applications>Accessories>Terminal: Run  
```
ifconfig
```
Can you use a USB stick or your network to copy the results of ifconfig here?

---

### Post by kellopoika on 2007-01-06
Thanks much for your message! I did have to restart, and I have a DSL connection . . .

Here are the results of ifconfig:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:254320 (248.3 KiB)  TX bytes:254320 (248.3 KiB)

---

### Post by ajgreeny on 2007-01-06
What were the updates installed, as I've just done the latest update and had no problems,

---

### Post by kellopoika on 2007-01-06
Here's where I have to make the embarrassing admission that I simply installed all that were available . . . 13 in toto :redface:

---

### Post by louieb on 2007-01-06
13 updates should not be a problem. I not an internet connection wizard. But I do have a  couple of things for you to check. 

System>Administration>Networking
Click on internet connection then click on properties.
Make sure the box enable this connection is checked.
And make sure The configuration drop down is set to DHCP.
Your ifconfig look like the IP is runing because you have a loopback address. But it does not look like your NIC is enabled. 

 Wired or wireless connection? If its wireless then I am clueless since I use wired.

But by way of reference here is what my ifconfig looks like and you can see the difference between mine and yours.
```
lou@gameu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:AB:19:BC:A8
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:abff:fe19:bca8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4534569 (4.3 MiB)  TX bytes:426875 (416.8 KiB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1032 (1.0 KiB)  TX bytes:1032 (1.0 KiB)

lou@gameu:~$

```

---

### Post by LuftFan on 2007-01-06
I have exactly the same problem.  Machine worked beautifully, I ran the updates and reboot.  Then it complained about something (MIME??? - not sure), but I didn't take notice. I wanted to get onto the net because I'm busy setting up another linux machine.

The next problem after the complaint was that my desktop wallpaper disappeared.  No problem to get that back but then the revelation.  No network!!!!

The machine dual boots to XP and there everything works fine so it is definelty not a coincidental harware problem.  

I do not see anything changed from before in the network setup.

More advice please!

Thank you,

LuftFan

---

### Post by LuftFan on 2007-01-06
I should add that I'm on Ubuntu 6.10 32-bit desktop.

---

### Post by kellopoika on 2007-01-07
Thanks very much  to all for your help! I tried reconfiguring my ethernet connection, and regained the connection. 

All the best,

Grant

---

### Post by LuftFan on 2007-01-07
I got back online after switching off my router and modem and do complete system restart once they were up again.
 
Baffled but at least it works again.  Now back to configuring my home network...

---

