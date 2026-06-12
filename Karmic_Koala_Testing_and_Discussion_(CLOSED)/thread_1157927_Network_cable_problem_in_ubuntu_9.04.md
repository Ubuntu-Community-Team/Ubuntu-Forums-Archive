---
title: "Network cable problem in ubuntu 9.04"
date: 2009-05-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by abhi_69 on 2009-05-13
[SIZE=3][FONT=Arial]hello members,
i am a regular user of ubuntu & recently i install ubuntu 9.04 in my desktop as default OS (i have windows also). i have a High Speed LAN internet connection in my PC. it works well in windows & it also works in ubuntu 8.10, fedora 10, mandriva 2009 etc (i test them all). but, in new ubuntu 9.04, i found a problem.
it can't detect my network connection automatically & show that 'network cable is disconnected or no network connection'. so, i manually enter my internet connection settings (IP address, DNS servers, subnet mask etc.). but alas! it still can't connect to internet & show 'no network connection'.
but, when i remove my network cable (CAT-6 cable) from CPU & after few times connect it again...this time it say 'connection established' & i can browse internet as usual. every time, i log in to ubuntu i am facing the same proeblem. so, every time i have to disconnect & re-connect my network cable to get internet connection. it is really annoying!!!
is it a bug of ubuntu 9.04? is their any solution to fix this problem? i want to browse internet without this problem.
any help for me?
thanks in advance.
[/FONT][/SIZE]

---

### Post by Peter09 on 2009-05-13
Its worth changing the cable in case that is faulty

---

### Post by abhi_69 on 2009-05-13
> **Peter09 said:**
> Its worth changing the cable in case that is faulty
it seems my cable is ok. this problem happening only in ubuntu 9.04. not in windows or fedora. any other solution for me?

---

### Post by Peter09 on 2009-05-13
Plug it in with no connection and provide the output of

```
ifconfig
```

```
route
```

---

### Post by abhi_69 on 2009-05-13
> **Peter09 said:**
> Plug it in with no connection and provide the output of

```
ifconfig
``````
route
```

Here is the output of 'ifconfig'-

----------------------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:16:76:cf:75:88  
          inet addr:192.168.100.2  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fecf:7588/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5201 (5.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1876 (1.8 KB)  TX bytes:1876 (1.8 KB)
-----------------------------------------------------------------------

and, here is the output of 'route'-

----------------------------------------------------------------
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

---------------------------------------------------------------

both output is taken when there is 'no connection'; but network cable is plugged with CPU. any help for me?
thanks.

---

### Post by Peter09 on 2009-05-13
This might be the bug report - look at the last line for a fix.

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204)

Note that you have no gateway defined in route - which is most probably the problem.

---

### Post by abhi_69 on 2009-05-14
> **Peter09 said:**
> This might be the bug report - look at the last line for a fix.

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/307204)

Note that you have no gateway defined in route - which is most probably the problem.
yes, i think so.
there is no gateway defined in route  (only a * sign) when cable is plugged but no connection. but, when i get connected,  i get the following output in 'route'-

----------------------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.100.1   0.0.0.0         UG    0      0        0 eth0
-------------------------------------------------------
here is a gateway defined with default destination (gateway- 192.168.100.1).

u said me to look at the last line for a fix. but, i can't understand actually which method i should try. can u help me? plz. tell me which method i should try. give me details. i never face this kind of network problem before. any help?
thanks in advance.

---

### Post by Peter09 on 2009-05-14
Well try
> 
Commenting out lines relating to  in dhclient.conf fixed the issue as well.```
gksudo gedit /etc/dhclient.conf
```put a # in front of rfc3442 and save the file

restart computer

---

### Post by abhi_69 on 2009-05-14
> **Peter09 said:**
> Well try
```
gksudo gedit /etc/dhclient.conf
```put a # in front of rfc3442 and save the file

restart computer
i follow ur method.
there is no 'dhclient.conf'  file in /etc folder. its in /etc/dhcp3 folder. by the way, i found no line starting with 'rfc3442' in this file. can u tell me actually which line i should uncomment with a # sign?
i get a line start like this-

option rfc3442..........................

i put a # in front of this line. but, the problem still there.
can u help me?
thanz.

---

### Post by Iowan on 2009-05-14
I noticed that addition to /etc/dhcp3/dhclient.conf.  There's the definition line, then a request line. The definition line can be commented out, but the request may need to be deleted.  I plan to try it - but I plan to make a backup of the file first. ;)

[update] Well, it seems to have worked - at least when it booted this time...
Peter09: I'm gonna link to your "fix" in my [thread]("http://ubuntuforums.org/showthread.php?t=1156441").

---

### Post by abhi_69 on 2009-05-16
> **Iowan said:**
> I noticed that addition to /etc/dhcp3/dhclient.conf.  There's the definition line, then a request line. The definition line can be commented out, but the request may need to be deleted.  I plan to try it - but I plan to make a backup of the file first. ;)

[update] Well, it seems to have worked - at least when it booted this time...
Peter09: I'm gonna link to your "fix" in my [thread]("http://ubuntuforums.org/showthread.php?t=1156441").
i tried this. but, not working at all! problem still there.
when i boot windows first & then reboot & switch to ubuntu, internet works well. but, if i boot into ubuntu first, network manager panel applet shows that 'Auth 0 is connected', but actually there is no connection. when i open browser & try to surf the internet it show error that-
'proxy server refuse connection' (becoz i use a proxy for internet)
i also try ping, its not working. so, i have to disconnect the cable & re-connect again to get it work. what can i do now? 
recently, this problem effecting my windows installation also. when i get internet connection in ubuntu & browse for sometimes, then i switch to windows it shows-
'network cable is unplugged' in windows also. but, after 10-12 sec it automatically get connected.
can anybody help me to fix this network problem?
regards.

---

### Post by measekite on 2009-06-12
> **Peter09 said:**
> Well try
```
gksudo gedit /etc/dhclient.conf
```put a # in front of rfc3442 and save the file

restart computer

What does this do?

On a reboot in order for me to connect to the wireless network I have to left click the icon in the system tray and then select connect to hidden network.  Then in the drop down select my connection and then press the connect button.  I am then good until I either reboot or logoff.

On a similar subject when I check **available to other users** at the bottom of the configuration dialog the connect button goes dark and inactive.  I had to create a new configuration for each user who uses the machine.

---

### Post by Ekeluo on 2009-10-09
I have this same problem, I think my LAN card's the same as the OP's. Anyone solve this.(Running Karmic Beta now).

---

### Post by bapoumba on 2009-10-10
Moved to Karmic.

---

### Post by w0o0zy on 2009-10-11
Hello

I have kind of the same problem too.
My laptop doesn't recognize at all the network cable. The network card led is not flashing, like it wasn't even inserted. Still, on Windows (7) it works.

What's the problem? I have Kubuntu 9.04.

Could you please tell me step by step what to do, because I had Kubuntu installed a year ago and I can't quite remember everything I knew back then, so I'm a noob again. By the way, I reinstalled Kubuntu because my internet is limited and I can't download torrents - I live in a college dorm now and the internet works through proxy and the admins have limited the torrents permanently.

But, a friend of mine told me that he managed to download torrents when using Linux. So I got back to Kubuntu. Why is it not recognising that my network cable is plugged?

---

