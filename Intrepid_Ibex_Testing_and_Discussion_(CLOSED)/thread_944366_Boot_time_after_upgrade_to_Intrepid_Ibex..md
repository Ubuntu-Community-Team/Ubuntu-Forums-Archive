---
title: "Boot time after upgrade to Intrepid Ibex."
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dhazin on 2008-10-11
I've updated my hardy installation to intrepid beta recently.
Right after upgrade I noticed that boot process became much more slow than before, it was ~ 1 minute.
I've tried to optimize boot process (including booting with profile option, yes I know that it can break readahead), but the best I could get so far is 30 sec that I think is too much for my system. Regarding readahead, I tried booting with or without readahead, create custom readahead lists, but the difference was not more than 1 sec anyway.
So the first question is: how can I speed up my boot process, what is the bottleneck (attached is my bootchart diagram) and how can I 'fix' readahead if it really affects boot time significantly.
Next, I could live with those 30 sec, but gnome desktop itself now loads much more slower than before. How is it possible to find and fix problems that cause all these slowdowns?
Any help greatly appreciated!

---

### Post by dhazin on 2008-10-12
Any ideas please? Especially regarding slow Gnome startup - I suspect that the reason can be screenlet (Clock) that is used, but how can I find out the real problem? Should I look into .xsession-errors or somewhere else?

---

### Post by plun on 2008-10-12
Bootchart is nearly indentical for me.

Gnome is slow and I don't start any 3rd party apps except AWN

This is a typical xsession-errors for me, spits out a lot..

[http://paste.ubuntu.com/56720/](http://paste.ubuntu.com/56720/)


Mismatch and race conditions for several functions...

---

### Post by autocrosser on 2008-10-12
I have noticed that with a new install the bootup is very fast--I would suspect that something in your old install is holding you back--Is there anyway you can do a fresh install to verify?

---

### Post by plun on 2008-10-12
> **autocrosser said:**
> I have noticed that with a new install the bootup is very fast--I would suspect that something in your old install is holding you back--Is there anyway you can do a fresh install to verify?

I found an error directly because of this thread.... :)

Unable to create /home/plun/.dbus/session-bus

Root has "conquered" it...    Testing. :)

---

### Post by dhazin on 2008-10-12
> **autocrosser said:**
> I have noticed that with a new install the bootup is very fast--I would suspect that something in your old install is holding you back--Is there anyway you can do a fresh install to verify?
Yes, the boot-up time improvements were on the list for 8.10 release and I'm quite sure that it will work for fresh install. But what's happening when upgrading?? If something old is holding back, probably it's possible to reinstall/reconfigure some packages?

---

### Post by ktp on 2008-10-12
I have also noticed boot time being longer than hardy. I would also like to know how to improve both boot and gnome startup.

---

### Post by funnypanks on 2008-10-12
> **ktp said:**
> I have also noticed boot time being longer than hardy. I would also like to know how to improve both boot and gnome startup.

since kde4 was updated to 4.1.2 its boot time is even worse than gnome. so moving to gnome has been quite nice. if we can make it boot faster that would be great

---

### Post by shane19174 on 2008-10-12
This would interest me as well. I upgraded from Hardy and noticed a serious slowdown both with the boot and the initial loadup of Gnome.

A few novice questions:

How do I create a boot chart? And where do I find a boot log?

Thanks in advance,
Shane

---

### Post by aethralis on 2008-10-12
sudo apt-get install bootchart

Then reboot and look in /var/log/bootchart

---

### Post by shane19174 on 2008-10-12
Thanks, aethralis. And what about a detailed log of the boot (including any errors covered over by the bootsplash)?

Thanks again,
Shane

---

### Post by aethralis on 2008-10-12
You could look at dmesg or it's easier to use dmesg > dmesg.txt and then look at it in gedit (it tends to be quite long).

---

### Post by psyke83 on 2008-10-12
Thirty seconds is pretty respectable.

From a quick look at your bootchart, I don't see any serious periods of inactivity. Your disk throughput is maximized for about 8-9 seconds during readahead, and modprobe maxes your CPU for 2-3 seconds, as it should. The rest of the boot doesn't interrupt save for some 1/2 second dips in throughput and CPU usage.

---

### Post by shane19174 on 2008-10-12
Dmesg.txt shows a couple of long pauses. I would appreciate it if someone could look at this (the end of the log; if more is needed let me know):

```
[   40.528146] wlan0: associated
[   40.530036] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.530270] wlan0: disassociating by local choice (reason=3)
[   44.962432] hda-intel: Invalid position buffer, using LPIB read method instead.
[   51.413019] wlan0: no IPv6 routers present
[   74.034207] canberra-gtk-pl[6243]: segfault at 12231ed8 ip b716e84d sp b6f14f10 error 6 in libpulse.so.0.4.1[b712f000+4e000]
[   81.784710] wlan0: authenticate with AP 00:1c:4a:4d:90:92
[   81.786720] wlan0: authenticated
[   81.786732] wlan0: associate with AP 00:1c:4a:4d:90:92
[   81.789717] wlan0: RX AssocResp from 00:1c:4a:4d:90:92 (capab=0x411 status=0 aid=1)
[   81.789728] wlan0: associated
[  144.919829] type=1503 audit(1223835629.495:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6724/net/" pid=6724 profile="/usr/sbin/cupsd"
[  145.953391] type=1503 audit(1223835630.531:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6730/net/" pid=6730 profile="/usr/sbin/cupsd"
[  145.953460] type=1503 audit(1223835630.531:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  145.953474] type=1503 audit(1223835630.531:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  145.953494] type=1503 audit(1223835630.531:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  145.953507] type=1503 audit(1223835630.531:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  145.953519] type=1503 audit(1223835630.531:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  145.953539] type=1503 audit(1223835630.531:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  145.953552] type=1503 audit(1223835630.531:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6730 profile="/usr/sbin/cupsd"
[  146.288701] ppdev0: registered pardevice
[  146.336544] ppdev0: unregistered pardevice
[  146.416219] ppdev0: registered pardevice
[  146.464064] ppdev0: unregistered pardevice
[  147.158964] ppdev0: registered pardevice
[  147.204248] ppdev0: unregistered pardevice
```

Thanks in advance,
Shane

---

### Post by inportb on 2008-10-12
Yeah, I have a feeling that it might be related to residual configuration as well. I'd originally kept my home directory but it was pretty slow. When I reinstalled to test the beta installer, I decided to rename my home directory and start over; it became quite fast then.

---

### Post by ercdvs on 2008-10-13
I am having a very similar issue, but I'm not sure how to go about troubleshooting it.

It looks like my boot time is affected here in dsmg 

One major cause is related to bug [#248577]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/248577")

  151.011650] NET: Registered protocol family 17
[  227.227554] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)

but earlier in the file I see :

9.555597] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xfa0b1, caps: 0xa04713/0x200000
[   19.591125] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   20.940405] lp: driver loaded but no devices found
[   21.149248] Adding 2377580k swap on /dev/sda5.  Priority:-1 extents:1 across:2377580k
[  148.346613] EXT3 FS on sda1, internal journal
[  149.269043] type=1505 audit(1223938891.551:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=12125

127 seconds for the EXT3 FS journal?  Is this 100% disk based or something else going on ?

---

### Post by derrick81787 on 2008-10-21
I'm  having the same problem, but the step that takes so long at boot time is when it is "Configuring network interfaces...".  Everything else is really fast, but that step takes about as long as all the other steps combined.  It's only happened since my update to Intrepid, and I have no idea what would be causing it.

- Derrick

---

### Post by Ramaddan on 2008-10-28
Same thing here.

After I upgraded from Hardy to Intrepid, I had this same problem.

It's all fine until it reaches:
> Configuring Network Interfaces
And then takes a long time before it continues.

The kernel used is:
> 2.6.27-7.14-generic

---

