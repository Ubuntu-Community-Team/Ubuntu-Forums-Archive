---
title: "[SOLVED] WICD update killed my networking"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Torquemada28 on 2008-09-30
On the 29/9/08, Adept found some updates, one of which was for the network connection manager WICD. I ran the updates overnight and when I checked my notebook in the morning, Adept said it couldn't commit the changes because of either a network problem or that it would break some dependencies. I checked the dependencies it listed and I don't have any of those packages installed. Ever since then, many programs won't load (such as Firefox and WICD) and the computername keeps vanishing from the hostname file. Oddly enough, when the hostname file goes blank, I can still use sudo, which isn't usually the case. I've tried manually setting my network up from System Settings>Network Settings but neither the ethernet and wireless networks will connect.

Can someone please point me in the right direction as I really don't want to have to do a reinstall (not before 8.10 is released anyway).

---

### Post by Torquemada28 on 2008-09-30
BTW
Ignore the system specs in my sig. They're for my home rig, not the notebook than I'm having trouble with (Acer Travelmate 4200).

---

### Post by imdano on 2008-10-01
The uninstall script of wicd 1.4.2 doesn't work right, so it fails to uninstall.  See this thread on how you can get wicd removed: [http://wicd.net/punbb/viewtopic.php?id=187](http://wicd.net/punbb/viewtopic.php?id=187)

I'm not exactly sure if that's the problem you're having without seeing the actual error message though.  Once you uninstall should be able to install the new version without any problem.  The new version is launched differently than the old one though, read about that [here](http://wicd.net/latest/changes).

Also, if you have an ethernet connection you can probably get the internet just by running ```
sudo ifconfig eth0 up
sudo dhclient eth0
```When the cable is plugged in.

---

### Post by Torquemada28 on 2008-10-02
Thanks imdano. The commands for getting ethernet up worked a treat.
I'm still working on the last suggestion in that thread.
> For ubuntu 8.04, if you had wicd on startup you simply need to go to system, preferences then session after that you just need to change the command for wicd that run on startup from /opt/wicd/tray.py or /opt/wicd/gui.py to wicd-client and that's it enjoy.
The previous suggestions haven't worked so I'm keen to try this method. The problem is, these instructions were written for Ubuntu, not Kubuntu (which I'm using). 

I'm still green so I'm having trouble finding the equivalent system settings in Kubuntu.
If you could explain how to accomplish the above task in Kubuntu, I would be eternally grateful.

---

### Post by imdano on 2008-10-02
For starters, lets make sure that's all you have to do.  Try running ```
wicd-client
```from a terminal.  If wicd's tray icon appears in your taskbar, then you're all set.  I don't use Kubuntu so I'm really not sure how you update the autostart entries for it.  Where would you go if you wanted to set a program to start when you login?

---

### Post by Torquemada28 on 2008-10-02
I have tried deleting any signifigant files left over after uninstalling wicd but I still get an error when I try to reinstall (screenshot attached).

Here is the contents of the log file located at /var/log/wicd/
```
2008/10/02 14:20:13 :: ---------------------------
2008/10/02 14:20:13 :: wicd initializing...
2008/10/02 14:20:13 :: ---------------------------
2008/10/02 14:20:13 :: Configuration file not found, creating, adding defaults...
2008/10/02 14:20:13 :: Automatically detected wireless interface wlan0
2008/10/02 14:20:13 :: automatically detected wired interface eth0
2008/10/02 14:20:13 :: setting wireless interface wlan0
2008/10/02 14:20:13 :: setting wired interface eth0
2008/10/02 14:20:13 :: setting wpa driver wext
2008/10/02 14:20:13 :: Setting dhcp client to 0
2008/10/02 14:20:13 :: setting automatically reconnect when connection drops
2008/10/02 14:20:13 :: setting use global dns to False
2008/10/02 14:20:13 :: setting use global dns to boolean False
2008/10/02 14:20:13 :: setting global dns
2008/10/02 14:20:13 :: global dns servers are None None None
2008/10/02 14:20:13 :: Wireless configuration file not found, creating...
2008/10/02 14:20:13 :: Wired configuration file not found, creating a default...
2008/10/02 14:20:13 :: Creating wired profile for wired-default
2008/10/02 14:20:13 :: chmoding configuration files 0600...
2008/10/02 14:20:13 :: chowning configuration files root:root...
2008/10/02 14:20:13 :: Using wired interface...eth0
2008/10/02 14:20:13 :: Using wireless interface...wlan0
2008/10/02 14:20:13 :: autoconnecting... wlan0
2008/10/02 14:20:17 :: Attempting to autoconnect with wired interface...Putting interface down
2008/10/02 14:20:17 :: 
2008/10/02 14:20:17 :: Releasing DHCP leases...
2008/10/02 14:20:17 :: Setting false IP...
2008/10/02 14:20:17 :: Stopping wpa_supplicant and any DHCP clients
2008/10/02 14:20:17 :: Flushing the routing table...
2008/10/02 14:20:17 :: Putting interface up...
2008/10/02 14:20:17 :: Running DHCP
2008/10/02 14:20:17 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2008/10/02 14:20:17 :: Internet Systems Consortium DHCP Client V3.0.6
2008/10/02 14:20:17 :: Copyright 2004-2007 Internet Systems Consortium.
2008/10/02 14:20:17 :: All rights reserved.
2008/10/02 14:20:17 :: For info, please visit http://www.isc.org/sw/dhcp/
2008/10/02 14:20:17 :: 
2008/10/02 14:20:17 :: wmaster0: unknown hardware address type 801
2008/10/02 14:20:18 :: wmaster0: unknown hardware address type 801
2008/10/02 14:20:18 :: Listening on LPF/eth0/00:16:d4:ac:cf:88
2008/10/02 14:20:18 :: Sending on   LPF/eth0/00:16:d4:ac:cf:88
2008/10/02 14:20:18 :: Sending on   Socket/fallback
2008/10/02 14:20:18 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
2008/10/02 14:20:26 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
2008/10/02 14:20:26 :: DHCPOFFER of 192.168.0.56 from 192.168.0.2
2008/10/02 14:20:26 :: DHCPREQUEST of 192.168.0.56 on eth0 to 255.255.255.255 port 67
2008/10/02 14:20:26 :: DHCPACK of 192.168.0.56 from 192.168.0.2
2008/10/02 14:20:26 :: bound to 192.168.0.56 -- renewal in 259335 seconds.
2008/10/02 14:20:26 :: DHCP connection successful
2008/10/02 14:20:26 :: Connecting thread exiting.

```
Hopefully, someone can see something amiss in the log file.
If you need me to post other output, let me know.
Thanks in advance. :)

---

### Post by Torquemada28 on 2008-10-02
> **imdano said:**
> For starters, lets make sure that's all you have to do.  Try running ```
wicd-client
```from a terminal.  If wicd's tray icon appears in your taskbar, then you're all set.  I don't use Kubuntu so I'm really not sure how you update the autostart entries for it.  Where would you go if you wanted to set a program to start when you login?

I have no idea where I configure startup apps.

Anyway, I had partial success running the command you just gave me. Wicd started and had an icon in the taskbar but it didn't have anything for my wireless, only the wired connection. Wireless is enabled in the system settings.
Here is the output from the terminal when I try to do a refresh in wicd.
```
refreshing...
wired profiles found
Fatal Error: template index file is missing.
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 1769, in refresh_networks
    tempnet = WirelessNetworkEntry(x)
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 1033, in __init__
    self.advanced_dialog = WirelessSettingsDialog(networkID)
  File "/usr/lib/python2.5/site-packages/wicd/gui.py", line 532, in __init__
    self.encrypt_types = misc.LoadEncryptionMethods()
  File "/usr/lib/python2.5/site-packages/wicd/misc.py", line 214, in LoadEncryptionMethods
    raise IOError(e)
IOError: [Errno 2] No such file or directory: '/etc/wicd/encryption/templates/active'



```

Any ideas?

---

### Post by Torquemada28 on 2008-10-02
Just in case it'e relevant, here's the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:ac:cf:88
          inet addr:192.168.0.56  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:feac:cf88/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16570961 (15.8 MB)  TX bytes:3268505 (3.1 MB)
          Interrupt:20

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:bd:9e:00
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-BD-9E-00-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Torquemada28 on 2008-10-02
Yay! I got wicd working again. Now I don't have to boot into Vista to do my work!

For those playing the home game, here's how I solved my problem.

In the end, it turned out to be a problem with dpkg, not wicd itself. I noticed [THIS THREAD]("http://ubuntuforums.org/showthread.php?t=934621") which talks about apt-get failing on every install after it choked on one particular install. I opened Adept and tried installing a random package and got the same error as I have been getting when trying to reinstall wicd. This hinted that one of my updates (wicd) had got caught sideways.
Running 
```
sudo dpkg --configure -a
```
and then
```
sudo apt-get install -f
```
gave apt-get the Heimlich Maneuver and allowed it to complete the original update.

Isn't it annoying how obvious these things appear in retrospect?
It first had an issue after doing an update so the first thing I should've looked at was the app doing the update, not the app being updated. *slaps forehead*

In any case, thank you very much to imdano and Partyboi2.

---

