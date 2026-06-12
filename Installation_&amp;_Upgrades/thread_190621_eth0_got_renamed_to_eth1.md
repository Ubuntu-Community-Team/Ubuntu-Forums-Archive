---
title: "eth0 got renamed to eth1"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by jchau on 2006-06-06
[COLOR="Red"]Correction to title: eth0 got renamed to eth2[/COLOR]

My ethernet interface formerly eth0 got renamed to eth2 after the upgrade to Dapper.  How do I get eth2 to become eth0 again?

My /etc/iftab file is the following:
```
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:14:22:fd:32:66
eth1 mac 00:13:ce:52:af:03

```
So I'm thinking that it should be eth0, but it isn't.

Help!
Thank you. (ifconfig does not show either eth0 or eth1 --probably because it is "not configured", but there is a screenshot attached which shows it)

---

### Post by John.Michael.Kane on 2006-06-06
This is a long shot since it only happened once to me. try deactivating the the wireless. rebooting then reactivate the wireless. it should now be seen as it should. as i said it's a longshot that worked for me.

---

### Post by jchau on 2006-06-06
Nope that doesn't work. Thanks though.  

Any other suggestions will be great.

---

### Post by mistamcgoo on 2006-06-06
i am stuck with the same problem, both my wifi nics (pcmcia linksys 11mbps on my laptop  and us robotics 54 mbps usb stick on my desktop pc) are installed with ndiswrapper, which installs these devices with device name wlan0 (with the ndiswrapper -m command)
. now with dapper they are called both eth1. the installation with ndiswrapper works completely, but i am 99% sure because of these different aliases the iwconfig wlan0 essid default key xxxxxxxxxx
command always give some kind of error (it tells me there is no device called wlan0), and if i try eth1 it gives me unknown error 254 because ndiswrapper doesnt recognize the eth1 alias. 
after googling around i found out about an ifrename and udev commands to rename eth1 to wlan0, this ifrename command works in breezy, but in dapper it returns "command not found? why is this command no longer available in dapper? 
i am almost 100% sure ifrename the device to its proper name would have fixed these problems, 
Why did the developers do this? If there's no way to fix this there will be lots of people without wifi. I'd feel very dissapointed if i had to downgrade again to breezy if i want my nic's to work.
btw, there are more topics on this problem already
[http://www.ubuntuforums.org/showthread.php?t=189526](http://www.ubuntuforums.org/showthread.php?t=189526)

---

### Post by jchau on 2006-06-06
I have a startling revelation:

After a bit of playing around, I decided to bring this new eth2 (formerly eth0) up.  When I couldn't get anywhere, I decided to check /etc/iftab again.  Since eth2 is up, I decided to check ifconfig too.

Here is /etc/iftab:
```
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:14:22:fd:32:66
eth1 mac 00:13:ce:52:af:03

```

Here is the output from ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:13:CE:52:AF:03
          inet addr:192.168.0.235  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe52:af03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:267503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15744035 (15.0 MiB)  TX bytes:1695082 (1.6 MiB)
          Interrupt:201 Base address:0xc000 Memory:dfcff000-dfcfffff

eth2      Link encap:Ethernet  HWaddr 00:14:22:FC:AD:B0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4293 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:803912 (785.0 KiB)  TX bytes:803912 (785.0 KiB)

```

If you compare the MAC or HW address of eth2 and its former name eht0, you'd probably notice that they are different.  

I considered the possibility that the upgrade caused something to change in /etc/iftab so I decided to check a backup from before the upgrade:
```
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:14:22:fd:32:66
eth1 mac 00:13:ce:52:af:03

```

Which showed me that the file did not change at all. Rather, the MAC address of the ethernet card changed.  Why would the upgrade do this?

Well, I'm going to investigate this further.  Any enlightment will be great!

---

### Post by jchau on 2006-06-06
OK. I realized that the MAC address change is probably due to some recent repairs.  I updated /etc/iftab with the new MAC address, and it works fine now.  Thanks for all the help:D

---

