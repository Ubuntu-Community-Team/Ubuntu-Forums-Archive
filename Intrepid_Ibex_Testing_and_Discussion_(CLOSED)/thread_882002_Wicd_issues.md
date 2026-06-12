---
title: "Wicd issues"
date: 2008-08-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LittleKoy on 2008-08-06
Since last mass updates, my wireless is not working anymore. Wicd doesn't connect automatically, and when I try to launch it using shell, this is what I get:

mesh@mesh-desktop:/etc/init.d$ sudo wicd-client 
Loading...
Attempting to connect tray to daemon...
Can't connect to the daemon, trying to start it automatically...
/var/run/wicd/wicd.pid
Attempting to connect tray to daemon...
Success.
ERROR:dbus.proxies:Introspect error on :1.36:/org/wicd/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 557, in <module>
    main(sys.argv)
  File "/usr/lib/wicd/wicd-client.py", line 538, in main
    tray_icon = TrayIcon(use_tray, animate)
  File "/usr/lib/wicd/wicd-client.py", line 102, in __init__
    self.icon_info = self.TrayConnectionInfo(self.tr, use_tray, animate)
  File "/usr/lib/wicd/wicd-client.py", line 121, in __init__
    self.update_tray_icon()
  File "/usr/lib/wicd/wicd-client.py", line 178, in update_tray_icon
    [state, info] = daemon.GetConnectionStatus()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.36 was not provided by any .service files

Any idea? Being without internet is the worst T_T
I tried NM too, and it started, but since it doesn't connect (it never did) it's quite useless :P

---

### Post by BC7333 on 2008-08-06
From a long time WICD user, try NM 0.7

---

### Post by _oOMOo_ on 2008-08-06
I just installed WICD 1.4.1 on an up-to-date Intrepid and it works fine. I can't use Network Manager as it doesn't work with the legacy ralink driver I need.

Which version of WICD are you running? Which wireless card/driver do you have?

---

### Post by LittleKoy on 2008-08-07
Well, I had this problem with 1.4.1, so I tried to upgrade to 1.5.1, but nothing changed. 
About my card, I have D-Link one, but I can't remember the number. I've used ndiswrapper until last month, now happily substituted with ath5k.

Yesterday I tried NM, but on Ubuntu Packages site the latest I could get was 0.6.6... How do I get 0.7?

---

### Post by LittleKoy on 2008-08-07
Furthermore, this morning my wcard isn't even getting the wireless connection, while yesterday, when I installed NM, it did (but didn't connect)

Edit: I tried NM 0.7, but it still can't connect. Could get the available connections, though

---

### Post by syko21 on 2008-08-07
Post your wireless card model info. Or if you are unsure which it is post the outputs of lspci and lsusb.

---

### Post by LittleKoy on 2008-08-07
The first says:

Atheros AR5416 802.11abgn Wireless PCI Adpter (rev 01)

My wcard is pci, so I don't think you need the 2nd...

---

### Post by mensonge on 2008-10-12
I had the same problem as you.
Try in a terminal:
```
sudo dpkg --configure -a
```

as explained into [http://ubuntuforums.org/showthread.php?p=5892170](http://ubuntuforums.org/showthread.php?p=5892170)

---

### Post by funnypanks on 2008-10-12
> **LittleKoy said:**
> Since last mass updates, my wireless is not working anymore. Wicd doesn't connect automatically, and when I try to launch it using shell, this is what I get:

mesh@mesh-desktop:/etc/init.d$ sudo wicd-client 
Loading...
Attempting to connect tray to daemon...
Can't connect to the daemon, trying to start it automatically...
/var/run/wicd/wicd.pid
Attempting to connect tray to daemon...
Success.
ERROR:dbus.proxies:Introspect error on :1.36:/org/wicd/daemon: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Traceback (most recent call last):
  File "/usr/lib/wicd/wicd-client.py", line 557, in <module>
    main(sys.argv)
  File "/usr/lib/wicd/wicd-client.py", line 538, in main
    tray_icon = TrayIcon(use_tray, animate)
  File "/usr/lib/wicd/wicd-client.py", line 102, in __init__
    self.icon_info = self.TrayConnectionInfo(self.tr, use_tray, animate)
  File "/usr/lib/wicd/wicd-client.py", line 121, in __init__
    self.update_tray_icon()
  File "/usr/lib/wicd/wicd-client.py", line 178, in update_tray_icon
    [state, info] = daemon.GetConnectionStatus()
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.36 was not provided by any .service files

Any idea? Being without internet is the worst T_T
I tried NM too, and it started, but since it doesn't connect (it never did) it's quite useless :P
i had that installed at first, had the same problem with my broadcom card. then i downloaded the deb for 1.4.2, uninstalled 1.5.3 completely thru synaptic and installed the 1.4.2 deb... it works perfectly now!!
all previous versions can be found here. again i used 1.4.2
[http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460)

---

### Post by pognonec on 2008-10-22
I had a similar problem: on a Dell XPS 1330, on hardy, I was happily using Wicd. After upgrading to intrepid, wifi did not work anymore, and Wicd did not see my (unchanged) network. And since Wicd was on my laptop, network manager did not get installed during upgrade to intrepid...
To solve the issue, I simply install network manager through synaptic, that automatically got rid of Wicd.
And since the new network manager worked surprisingly well and easily, I kept it. 
But I guess you could then reinstall Wicd, which would likely work fine again, after removing network manager...there

---

