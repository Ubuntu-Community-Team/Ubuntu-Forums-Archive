---
title: "Network problems with interpid updates"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ReedMace on 2008-10-08
Two updates ago (=2 days ago) wireless network was working fine on intrepid. Manual configuration was retained on booting up, network was automatically connected, signal strength was excellent, internet connection was fine. Then I installed the latest updates and the network stopped. Manual configuration was still there but no network.

I plugged in an ethernet cable, manually configured this in Network Manager and managed to connect to the home network. However, network traffic only comes in bursts of 8 seconds every minute or so. The rest of the time there is no traffic and the application (eg firefox/update manager etc) has to wait for the next burst of activity. My other machine running windows on the same network has no such problems, so its not the network. Also, the manual configuration of the ethernet connection is lost on every re-boot.

I have tried following the sticky thread "How to: Manual Network Configuration..." but this does not work for me. The network interface name (which used to be wlan0 when I last manually configured it, several days ago) is now reported as wmaster0. When I enter the command

```
sudo dhclient -r wmaster0
```
I get the Intel copyright stuff (its a Pro/Wireless 4965 AG/AGN adapter) followed by

```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

```
When I enter the command

```
sudo ifconfig wmaster0 192.168.1.70 netmask 255.255.255.0 up
```

the following is returned

```
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported

```

When I try

```
sudo route add default gw 192.168.1.1
```

the response is

```
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
```
I really have no idea what is gong on here.

I have tried rebooting to earlier installations of Ubuntu from the GRUB menu but this makes no difference.

Can anyone help?

Hoping that I get a little more response to this post than I have to my previous vain attempts.

ReedMace

---

### Post by Sef on 2008-10-08
moved to ibex forum.

---

### Post by kforum on 2008-10-08
hi there, your network device is and always will be named wlan0(i have that wifi card too). wmaster0 is more of a place holder of sorts...

you can read about it here:
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-11/msg04355.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-11/msg04355.html)
or here:
[http://ubuntuforums.org/showthread.php?t=781427](http://ubuntuforums.org/showthread.php?t=781427)
leading to this link(search wmaster0) here:
[http://linuxwireless.org/en/developers/Documentation/mac80211](http://linuxwireless.org/en/developers/Documentation/mac80211)

so in other words, you, or the update, broke something.

maybe your wireless is disabled, or deleted.

can you do ifconfig, and lets see what shows up?
or check on your network interfaces file.(not sure where this is in debian, i can check. first ill need that ifconfig, to be sure).


on a side note, i myself havent been able to connect through wifi, ever since i install the beta(from scratch), but i think its mainly a knetmanager issue, so it should prob. work if its manually set. ^^


cheers.

---

### Post by ReedMace on 2008-10-10
Thanks for the links. I notice here that lots of others are having problems with the updates.

Interestingly I have a similar problem to andreselsuave ([[COLOR="Blue"]_http://ubuntuforums.org/showthread.php?t=781427_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=781427")). Network is being reported as DISABLED. Entering the code suggested by chili555:

```
sudo cat /var/log/messages | grep Kill
```
 reports the following:
```
Oct  7 16:58:13 hydrology-laptop kernel: [12694.459934] iwlagn: Radio Frequency Kill Switch is On:
Oct  7 16:58:13 hydrology-laptop kernel: [12694.459934] Kill Switch must be turned off for wireless networking to work.
Oct  7 17:40:25 hydrology-laptop kernel: [  446.525532] iwlagn: Radio Frequency Kill Switch is On:
Oct  7 17:40:25 hydrology-laptop kernel: [  446.525532] Kill Switch must be turned off for wireless networking to work.
```

So why is the Kill Switch on and how do I turn it off?

Thanks

ReedMace

---

### Post by ReedMace on 2008-10-12
Hello?

Does anyone know how to turn this kill switch off?

ReedMace

---

### Post by daahli on 2008-10-12
I had a similar problem. Believe it or not installing and running firestarter solved all issues, no idea why. Hope that helps you guys.

---

### Post by ReedMace on 2008-10-13
Installing Firestarter has not helped, but thanks for the suggestion.

Ipconfig output is as follows:

```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:6d:2c:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178416 (178.4 KB)  TX bytes:178416 (178.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:da:50:db  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:feda:50db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115449 (115.4 KB)  TX bytes:7266 (7.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-DA-50-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

wlan0 still does not appear, however, in the network manager and I have no access to the wireless network

Can someone help with this or the Kill Switch issue?

Reedmace

---

### Post by nystire on 2008-10-13
Is there no physical switch for your network card, perhaps? Maybe on the front of the laptop or above the keyboard?

---

### Post by hind3nburg on 2008-10-13
I also saw some network issues a couple days ago with an update. My wireless dropped out and wouldn't reconnect and but my nic was fine. A reboot solved that issue though.

---

### Post by nystire on 2008-10-13
> **ReedMace said:**
> Installing Firestarter has not helped, but thanks for the suggestion.

Ipconfig output is as follows:

```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:6d:2c:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178416 (178.4 KB)  TX bytes:178416 (178.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:da:50:db  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:feda:50db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115449 (115.4 KB)  TX bytes:7266 (7.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-DA-50-DB-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

wlan0 still does not appear, however, in the network manager and I have no access to the wireless network

Can someone help with this or the Kill Switch issue?

Reedmace

wlan0 DOES appear in that output. The second one from the end.

---

### Post by ReedMace on 2008-10-13
> **nystire said:**
> Is there no physical switch for your network card, perhaps? Maybe on the front of the laptop or above the keyboard?
Wireless switch is on.

I have rebooted so many times it is getting very tedious. In order to connect to the internet I have to re-enter the network settings for the ethernet connection every time after plugging the cable back in (I unplug each time to see if the wireless works THIS time).

ReedMace

---

### Post by nystire on 2008-10-13
Going out on a limb here, but maybe "sudo apt-get purge network-manager" (answer yes to allow it to remove network-manager-gnome too) and then reinstall both of them with "sudo apt-get install network-manager-gnome"?

---

### Post by ReedMace on 2008-10-13
I know wlan0 appears in the ipconfig output, but I was referring to the Network Manager, where it does NOT appear.

ReedMace

---

### Post by ReedMace on 2008-10-13
> **nystire said:**
> Going out on a limb here, but maybe "sudo apt-get purge network-manager" (answer yes to allow it to remove network-manager-gnome too) and then reinstall both of them with "sudo apt-get install network-manager-gnome"?

Is this safe to do??

---

### Post by nystire on 2008-10-13
It should be, assuming you don't unplug the network cable in between the two commands. The second one reinstalls the packages which the first one removes

---

### Post by ReedMace on 2008-10-13
The install hasn't worked. The network became unavailable and none of the archives could be found. I now have no network on that machine even through the cable.

Network Tools is still there, but I can't do anything with that. However, wlan0 is listed in it as a network device, and if I select it, I can successfully ping my modem. So there is a connection there. I can even access my modem's html interface in firefox. However, I can't seem to access the internet, and none of the archives or updates can be found.

Any ideas on how to proceed from here?

ReedMace

---

### Post by cl333r on 2008-10-13
the network manager is a mess, I think it's time to fix it. Childish bugs such as not remembering config is ridiculous.

---

### Post by nystire on 2008-10-13
It sounds like the routes are not being set up correctly.

Download the two .deb files from here on another pc:
[http://packages.ubuntu.com/intrepid/i386/network-manager-gnome/download](http://packages.ubuntu.com/intrepid/i386/network-manager-gnome/download)
[http://packages.ubuntu.com/intrepid/i386/network-manager/download](http://packages.ubuntu.com/intrepid/i386/network-manager/download)

Then install them with "sudo dpkg -i network-manager*.deb"

That should return you to the original state.

---

### Post by ReedMace on 2008-10-14
I have now managed to get the wireless network working again in the absence of the Network Manager. The issue seems to have been a mixture of mis-reporting by various programs and the Network Manager not doing what it says on the tin - in my case.

The primary problem in my case (in case anyone else has a similar problem) was that the search domain ("workgroup" in Windows parlance) and DNS server had become dislocated from my wireless configuration, despite being set up in the Network Manager. After uninstalling NM I still had the Network Tools and was able to ping both my router and my modem, and even the Google UK site (64.233.179.99), although NOT the ubuntu site (82.211.81.158 ) recommended ([_http://help.ubuntu.com/8.04/internet/C/troubleshooting.html_]("http://help.ubuntu.com/8.04/internet/C/troubleshooting.html")), which doesn't appear to exist at that address - so that's a bit unfortunate if you're trying to use it to troubleshoot.

Successfully pinging the Google site, however, meant I had a connection to the world outside, and the fact the Firefox couldn't interpret website names meant it must be a Domain Name Server issue (DNS). There is a very helpful guide on the [_ubuntu server network configuration pages_]("http://help.ubuntu.com/8.04/serverguide/C/network-configuration.html") which explains where to type some simple text into a configuration file, in /etc/resolv.conf

I confess being astonished when, after doing this, I had a working internet connection that I could use.

This is despite still being told that the Radio Frequency Kill Switch is on and must be turned off for wireless networking to work, and despite ```
lshw -C network
``` reporting that the logical name of my wireless device is wmaster0, not wlan0, and despite Network Manager (which I have since reinstalled) telling me (as it does at the moment) that networking is disabled.

All in all, some unhelpful stuff being reported. No wonder some of us are having difficulties. In my case.

ReedMace

---

