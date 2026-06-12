---
title: "nm-applet missing after upgrade to intrepid"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by doesntcount on 2008-10-23
I encountered a documented bug where vpn connections cannot be done with network manager when you have a manually configured wireless ethernet port (which I have). I discovered the bug was fixed in network-manager 0.7 which comes with intrepid, so I decided to upgrade to intrepid. 

The upgrade was a success, but suddenly, the nm-applet icon is missing from the panel. ps shows that it's running, but it's not in the panel.

Everything else is visible: calendar, sounds, etc. And I've double checked that it's started by gnome via System->Prefs->Sessions->Network Manager.

Seems like an intrepid bug. Should I submit it? Does anybody have work-around ideas in the mean time? Thanks for the help.

---

### Post by karlatsaic on 2008-10-23
I'm looking for similar advice. You should be able to start it manually in a terminal window with
"nm-applet --sm-disable" according to things I have read. Before you do that you might try:
"ps -aux | grep nm-applet" to see if the nm-applet is running. In my case, nm-applet IS running, but I get no icon in the Notification tray as usual. I also have a laptop with 8.04 and things are running normally and the ps command shows "nm-applet --sm-disable". On my laptop with the same problem noted here I just did an update to 8.10 (beta) and so I figure some configuration setting is just not right as I was running 8.04 previously. If there is no simple answer, I was just going to try a clean install of 8.10 (Intrepid) when it is finalized, but an interim solution is appreciated.

---

### Post by doesntcount on 2008-10-23
I too see nm-applet running according to ps. I tried killing it and starting it manually to see if that would get me anywhere, but I get this:

```

$ nm-applet --sm-disable

** (nm-applet:6087): WARNING **: Invalid connection: 'NMSettingIP4Config' / 'method' invalid: 2

** (nm-applet:6087): WARNING **: <WARN>  constructor(): Invalid connection: 'NMSettingWirelessSecurity' / 'proto' invalid: 1


** (nm-applet:6087): WARNING **: Invalid connection: 'NMSettingIP4Config' / 'method' invalid: 2

```

No idea what those warnings mean, but even after running this, still no icon in the tray with which to configure my network :(

---

### Post by Mr Fredrick on 2008-10-23
same problem here!

---

### Post by doesntcount on 2008-10-23
Pretty interesting that everyone that's seeing this problem has a laptop. I bet it has something to do with having a wired and a wireless interface or something like that.

In any case, I'm in a position where I have nothing to lose on my laptop (i've only very recently installed hardy) so I'm about to reinstall from scratch (no upgrade from hardy). I'll get back with those results shortly.

---

### Post by kjartan on 2008-10-24
ditto

krh@kjartan:~$ lspci|grep Network
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

krh@kjartan:~$ nm-applet --sm-disable

** (nm-applet:29095): WARNING **: Invalid connection: 'NMSettingIP4Config' / 'method' invalid: 2

** (nm-applet:29095): WARNING **: Invalid connection: 'NMSettingIP4Config' / 'method' invalid: 2

---

### Post by sammy_pal on 2008-10-24
Same problem here. Comapaq Presario V3018TU Laptop.
Wireless: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Wired Ethernet: Intel Corporation PRO/100 VE Network Connection (rev 02)

```
ps aux | grep nm-applet
``` shows nm-applet --sm-disable is running.
```
killall nm-applet
``` followed by ```
nm-applet --sm-disable
``` yields no results.
:confused: Is there any solution ?

---

### Post by rturner on 2008-10-24
> **karlatsaic said:**
> I'm looking for similar advice. You should be able to start it manually in a terminal window with
"nm-applet --sm-disable" according to things I have read. Before you do that you might try:
"ps -aux | grep nm-applet" to see if the nm-applet is running. In my case, nm-applet IS running, but I get no icon in the Notification tray as usual. I also have a laptop with 8.04 and things are running normally and the ps command shows "nm-applet --sm-disable". On my laptop with the same problem noted here I just did an update to 8.10 (beta) and so I figure some configuration setting is just not right as I was running 8.04 previously. If there is no simple answer, I was just going to try a clean install of 8.10 (Intrepid) when it is finalized, but an interim solution is appreciated.

My nm-applet is running, but no icon either.  I'm on a desktop, wired, and I notice everyone else in this thread is on a laptop.  I'll skip the long story about how a new video card borked my system, but I reinstalled 8.04 mainly because that was the only cd I had sitting around.  I set my static IP address and immediately upgraded to the Intrepid beta, which is when the network manager icon disappeared.  However, all my networking is working fine (better than on Hardy), but trying to run nm-applet errors out.  So, maybe a clean install will work, but it's not a wireless-only problem.

---

### Post by sammy_pal on 2008-10-24
Check this:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404)

Following the instructions helps.:)

---

### Post by JGrubbs on 2008-10-24
I added the following to my Software Sources when I first upgraded to Intrepid to get the network manager to work:

[http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
[http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

---

### Post by doesntcount on 2008-10-25
Before posting originally, I followed the instructions from sammy's link (kill nm-applet, start it with sudo) but that did not help.

I can confirm that I've installed from scratch (no upgrade from hardy) and I'm happy to report that the nm-applet is present, so that's good news.

The bad news for me is that original reason that I was upgrading in the first place was because network-manager .65 had a bug where you couldn't configure vpn and have a manually configured wireless network port (which I have). With intrepid (now that I can at least see nm-applet) I cannot configure the vpn because the +Add button on the write to configure a new vpn connection is greyed out.

Sigh, so much work for something that should be so simple.

I'll keep messing around and report bag when I have a solution.

---

### Post by doesntcount on 2008-10-25
Duh, i had to apt-get network-manager-pptp to configure vpn, but now that i've done that I've run into a connection issue that is discussed at great length here:

[http://ubuntuforums.org/showthread.php?t=922362&page=3](http://ubuntuforums.org/showthread.php?t=922362&page=3)

*sigh* I'm learning that VPN and Ubuntu aren't good friends. It didn't even cost me this much effort  to get vpn working on gentoo :(

---

### Post by baraba on 2008-10-25
Please post contents of file: /etc/network/interfaces

Cheers!

---

### Post by doesntcount on 2008-10-25
```
$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

Some good news however: I connected to the vpn with pon, had to manually setup some routes to get into the vpn network. But the connection was only open for 60s and then i was disconnected. I think i remember seeing a post about this somewhere, so I'll find that and see if it helps.

Unfortunate that this doesn't all work through nm-applet and that it doesn't stay connected. But if anybody has tips on that, I'm happy to try them out.

---

### Post by sammy_pal on 2008-10-25
Did you try this one-
[URL="https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404/comments/4"]https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/249404/comments/4
[/URL]

---

### Post by doesntcount on 2008-10-26
Hmm, I wonder if that would help everyone else that's been having issues. I worked around the problem by installing intrepid from scratch rather than upgrading from hardy.

---

### Post by kjartan on 2008-10-27
I'm still having problems with this issue.

```

krh@kjartan:~$ apt-cache policy dbus network-manager network-manager-gnome consolekit
dbus:
  Installed: 1.2.4-0ubuntu1
  Candidate: 1.2.4-0ubuntu1
  Version table:
 *** 1.2.4-0ubuntu1 0
        500 http://ftp.ds.karen.hj.se intrepid/main Packages
        100 /var/lib/dpkg/status
network-manager:
  Installed: 0.7~~svn20081018t105859-0ubuntu1
  Candidate: 0.7~~svn20081018t105859-0ubuntu1
  Version table:
 *** 0.7~~svn20081018t105859-0ubuntu1 0
        500 http://ftp.ds.karen.hj.se intrepid/main Packages
        100 /var/lib/dpkg/status
network-manager-gnome:
  Installed: 0.7~~svn20081020t000444-0ubuntu1
  Candidate: 0.7~~svn20081020t000444-0ubuntu1
  Version table:
 *** 0.7~~svn20081020t000444-0ubuntu1 0
        500 http://ftp.ds.karen.hj.se intrepid/main Packages
        100 /var/lib/dpkg/status
consolekit:
  Installed: 0.2.10-1ubuntu9
  Candidate: 0.2.10-1ubuntu9
  Version table:
 *** 0.2.10-1ubuntu9 0
        500 http://ftp.ds.karen.hj.se intrepid/main Packages
        100 /var/lib/dpkg/status

krh@kjartan:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

krh@kjartan:~$ cat /etc/dbus-1/system.d/NetworkManager.conf
<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="root">
                <allow own="org.freedesktop.NetworkManager"/>
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>

		<allow own="org.freedesktop.NetworkManager.PPP"/>
                <allow send_destination="org.freedesktop.NetworkManager.PPP"/>
                <allow send_interface="org.freedesktop.NetworkManager.PPP"/>
        </policy>
        <policy user="haldaemon">
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>
        </policy>
        <policy at_console="true">
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>
        </policy>
        <policy context="default">
                <allow own="org.freedesktop.NetworkManager"/>
                <allow send_destination="org.freedesktop.NetworkManager"/>
                <allow send_interface="org.freedesktop.NetworkManager"/>

                <allow own="org.freedesktop.NetworkManager.PPP"/>
                <allow send_destination="org.freedesktop.NetworkManager.PPP"/>
                <allow send_interface="org.freedesktop.NetworkManager.PPP"/>
        </policy>

        <limit name="max_replies_per_connection">512</limit>
</busconfig>

krh@kjartan:~$ uname -a
Linux kjartan 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux

krh@kjartan:~$ ps -ef|grep nm-applet
krh      21773  7083  0 13:29 pts/0    00:00:00 grep nm-applet

krh@kjartan:~$ sudo nm-applet --sm-disable
** (nm-applet:21783): WARNING **: No connections defined
^C** Message: Caught signal 2, shutting down...
krh@kjartan:~$ 

```

---

### Post by cowanh00 on 2008-10-27
I have managed to solve the issue where Network Manager doesn't show in the notification tray on startup. In my home folder I had a folder called .config and in there a folder called autostart which contained what seamed to be a loader for Network Manager. I deleted the autostart folder and rebooted and Network Manager shows in the tray now!

I hope this can help someone.

EDIT: Looks like I spoke too soon. After another restart it is the same problem. :-(

---

### Post by larsemil on 2008-10-28
> **kjartan said:**
> I'm still having problems with this issue.

```


krh@kjartan:~$ sudo nm-applet --sm-disable
** (nm-applet:21783): WARNING **: No connections defined
^C** Message: Caught signal 2, shutting down...
krh@kjartan:~$ 

```

i have the exact same problem on intrepid and my eeepc

it feels like i tried everything. i did do a netinstall though so it could be something else missing.. dont want to do a full install as i only have 4gb of harddrive. never had any problem in any older version of ubuntu

---

### Post by andylinux on 2008-10-28
I had the same problem and was able to fix it by doing as suggested,
adding this to my sources.list file,

[http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
[http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

---

### Post by wartalker on 2008-10-29
i have the same problem, how? i upgraded from 8.04, and is laptop.

---

### Post by reader4 on 2008-10-29
Having similar issue after upgrading from Hardy on my laptop w/ ipw2200. Networking actually worked just fine to begin with, but after some restart it stopped.  After going through bug reports, etc. and trying several things, I was able to get the nm-applet running again by deleting the autostart entry.  However, now I am told that networking is disabled despite "enable networking" being checked in the panel applet.  cat /etc/network/interfaces shows my wired connection (eth0) but does not show my wireless (eth1).  ifup eth1 dies with "Ignoring unknown interface eth1=eth1".  Not sure what else to try...

---

### Post by wartalker on 2008-10-29
i have reapir this problem, edit /etc/network/interfaces, just like this:

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0

---

### Post by cremase on 2008-10-29
> **wartalker said:**
> i have reapir this problem, edit /etc/network/interfaces, just like this:

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0

That worked for me too! :)
Thank you wartalker.

Bye,
Ezio.

---

### Post by larsemil on 2008-10-30
> **wartalker said:**
> i have reapir this problem, edit /etc/network/interfaces, just like this:

auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth0

well that does not help me. 
i still get 
```

larsemil@mamin:~$ nm-applet --sm-disable

** (nm-applet:5165): WARNING **: No connections defined
^C** Message: Caught signal 2, shutting down...

```

no idea what to do about this. anyone?

---

