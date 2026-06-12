---
title: "[SOLVED] Network bonding problem"
date: 2009-01-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-03
I am having a problem with my network bond.  Originally my DNS would sometimes not resolve while all the other PC's would still resolve (same DNS , my router).  I manually set the DNS to openDNS server and it has been alot better, but not flawless.  I still get long timeouts sometimes.  Also I noticed that my routing table is messed up (possible reason for DNS issues) it currently looks like this:

```

@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 bond0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 bond0
default         192.168.1.1     0.0.0.0         UG    0      0        0 bond0
@ubuntu:~$
```
I am not sure if I did something to change it, but I seem  to remember it looking different before:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 bond0
link-local      *               255.255.0.0     U     1000   0        0 bond0
default         192.168.1.1     0.0.0.0         UG    0      0        0 bond0

```
or something similar.  My /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth1
#iface eth1 inet dhcp

#added
auto bond0
iface bond0 inet static
        address 192.168.1.105
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255

        gateway 192.168.1.1
        up /sbin/ifenslave bond0 eth0 eth1
        down ifenslave -d bond0 eth0 eth1
```

Also, unrelated, I use Opera (Version 10 Build 4103) and noticed that I started to get random crashes sometimes.  At different times mostly, once when I tabbed in this forum, once when reloading a page, and twice from opening a new page.  Anyone else having any Opera problems?

---

### Post by LordVeovis on 2009-01-03
Fixed.  I accidently hit submit while I was jotting a note >.< had to *edit* to post.

---

### Post by ronacc on 2009-01-03
I had no problems with Opera 10 build 4103  and am having none with 4116  both 64 bit . question are the other pc's running jaunty ? if not see this thread ```
http://ubuntuforums.org/showthread.php?t=1026105 
```
and this bug ```
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313218 
```

---

### Post by marmuta on 2009-01-04
Looks like the eth devices have no gateway to route to. Have you tried deleting the eth0/1 routes manually?
Maybe network-manager added them there?

---

### Post by LordVeovis on 2009-01-05
> **marmuta said:**
> Looks like the eth devices have no gateway to route to. Have you tried deleting the eth0/1 routes manually?
Maybe network-manager added them there?

It seems that way to me to.  The network manager adding them that is.  I have deleted them manually, but they come back on their own without a reboot.  Same with the default gw eth1 entry.  every time it does i have to delete it again.  I opened the network manager and told it to not automatically connect, about to reboot and see if that was it.  I had not previously seen that option, its new as my 8.10 doesn't have it.

Also I was transferring files from one PC to another and was only getting about 25MB/sec speed with bonded gigabit nics on both PCs... that seems really slow?

Edit:  No change after reboot.  It will set it back to auto connect.  How can I disable that more permanently?

---

### Post by marmuta on 2009-01-06
Have you seen [bug #239999]("https://bugs.launchpad.net/network-manager/+bug/239999")?

Then I guess [that]("http://bugzilla.gnome.org/show_bug.cgi?id=558518") settles it:
> NM doesn't yet support bonded devices; for the moment I'd suggest either
turning off NetworkManager if the bonded devices are your primary internet
connection, or if they are not, making them unmanaged so that NM ignores them. 
Bonding is a feature we expect NM to support in the future...


About the speed, how did you measure it and is that a direct link between pcs? Otherwise the router may be the bottleneck there.

---

### Post by ShirishAg75 on 2009-01-06
I have a question, what are bonded connections or network bonding? Any links with any material to understand the concept would be nice. 

Also any use-case given would be good.

---

### Post by marmuta on 2009-01-06
Shirish, bonding/trunking means to combine a number of physical network interfaces (on linux e.g. ethx) into a new virtual device (linux bondx).
This can be done for a number of reasons, redundancy, load balancing or like what I believe LordVeovis is trying to do, to increase bandwidth. 

He is using bonding to combine eth0 and eth1 into bond0 which then theoretically would provide twice the bandwidth (but barely reaches the throughput of a single 1000BASE-T link).

Here is more: [wiki]("http://en.wikipedia.org/wiki/Link_aggregation"), [kernel.org]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/networking/bonding.txt;hb=HEAD")

---

### Post by LordVeovis on 2009-01-06
> **marmuta said:**
> Have you seen [bug #239999]("https://bugs.launchpad.net/network-manager/+bug/239999")?

...

About the speed, how did you measure it and is that a direct link between pcs? Otherwise the router may be the bottleneck there.

How can I have network manager ignore those 2 connections? If i disable networking in network manager it takes my cards offline so my bond fails.  And as I mentioned above setting it to not auto connect does nothing.

Second note, the speed was measured by what gnome told me.  I know that it is not at all a true representation of my bandwidth being used, but 25MBpS is still slow.  I was going to get a true app for testing network bandwidth but have not yet.  Any suggestions for an app to use?

---

### Post by LordVeovis on 2009-01-06
> **ShirishAg75 said:**
> I have a question, what are bonded connections or network bonding? Any links with any material to understand the concept would be nice. 

Also any use-case given would be good.

My bond is set for adaptive load balancing.  Which basically meant that it will try to balance the load across the NICs to increase speed at the cost of CPU overhead.  The additional benefit is that if a NIC fails, or the router / cables / etc. connected to one of the NICs fail the other NIC will take over as primary and allow you to keep network up at a reduced speed now.

All of this is handled at the cost of a little CPU overhead as the CPU intercepts packets and changes the addresses of the packet to make the destination send to the card it wants to receive on.  It's all kinda neat honestly.

EDIT: My spelling is poor sometimes...

---

### Post by ShirishAg75 on 2009-01-06
LordVeovis, 
 perhaps this is something you are looking for. 

There is a package called bandwidthd

```

Description: Tracks usage of TCP/IP and builds html files with graphs
 BandwidthD tracks usage of TCP/IP network subnets and builds html files with
 graphs to display utilization. Charts are built by individual IPs. Color Codes
 HTTP, TCP,UDP, ICMP, VPN, P2P, etc. 
 
 This is the static version, see bandwidthd-pgsql for multi sensor/php frontend
 bandwidthd.
Homepage: http://bandwidthd.sourceforge.net/

```You can install either the the stand-alone or the pgsql version 

```
bandwidthd - Tracks usage of TCP/IP and builds html files with graphs
bandwidthd-pgsql - Tracks usage of TCP/IP and builds html files with graphs
```either use synaptic or apt-get or aptitude to install the same.

The homepage has some nice screenshots of the same. 

[http://bandwidthd.sourceforge.net/](http://bandwidthd.sourceforge.net/)

This is just one, do a little search there are quite a few more.

---

### Post by marmuta on 2009-01-06
> **LordVeovis said:**
> How can I have network manager ignore those 2 connections? 
I believe what he means is to disable "Enable roaming mode" in network-admin. You would have to install gnome-network-admin to get that. I haven't bothered to find a non-gui way yet. Let me know if you happen to find one.

> I was going to get a true app for testing network bandwidth but have not yet.  Any suggestions for an app to use?
I like iperf for quick checks.
on server: iperf -s
on client: iperf -c <server-ip>

---

### Post by LordVeovis on 2009-01-06
> **marmuta said:**
> I believe what he means is to disable "Enable roaming mode" in network-admin. You would have to install gnome-network-admin to get that. I haven't bothered to find a non-gui way yet. Let me know if you happen to find one.


I like iperf for quick checks.
on server: iperf -s
on client: iperf -c <server-ip>

If I disable "Enable Roming Mode" I have to set a connection type.  DHCP / Static, etc. (if I remember correctly)  I tried to do this on the 8.10 machine.  With a bond you dont want the cards to have thier on individual IPs

---

### Post by marmuta on 2009-01-07
Yes ... but ... the goal was to stop networkmanager from interfering.
network-admin AFAIK does nothing behind your back. Just choose anything, but make a backup of /etc/network/interfaces beforehand, because this is where it writes too.

You can afterwards edit /etc/network/interfaces to your hearts content, at least the non-roaming interfaces.
If I knew what "Enable roaming mode" mapped to we could have skipped this step.

If then networkmanager still doesn't play ball, well, time to yank it, but you should in any case raise this issue on [networkmanager-list]("http://mail.gnome.org/mailman/listinfo/networkmanager-list") to let them know there is interest in port bonding.

---

### Post by LordVeovis on 2009-01-07
> **marmuta said:**
> Yes ... but ... the goal was to stop networkmanager from interfering.
network-admin AFAIK does nothing behind your back. Just choose anything, but make a backup of /etc/network/interfaces beforehand, because this is where it writes too.

You can afterwards edit /etc/network/interfaces to your hearts content, at least the non-roaming interfaces.
If I knew what "Enable roaming mode" mapped to we could have skipped this step.

If then networkmanager still doesn't play ball, well, time to yank it, but you should in any case raise this issue on [networkmanager-list]("http://mail.gnome.org/mailman/listinfo/networkmanager-list") to let them know there is interest in port bonding.

Well I just installed over the 8.10 I had on the second box.  Wanted to look at fedora on it, have jaunty on my main box and just got an el-cheapo laptop and I put 8.10 on it (but nvidia doesn't play nice... I forget how to set the resolution manually in xorg.conf, i think the default it sets is to high) so I have just the vesa i think. I may try fedora there and put Free BSD - zfs support I hear? - on my PC sporting fedora. (And Slackware at work - not a fan tho.)

Anyways, as far as jaunty goes tho, you think I should install network-manager and give that a go by disabling that and then manually make the interfaces file? I'll give it a shot and post how it looks.

EDIT: It says I have network-manager installed.  I can't run it nor can I find it.  I tried:
```

find / -iname network-manager

```
No luck.

EDIT: Free BSD is a no go on my other box :(  Requires ps2 kybd install??? I have a dell xps that has no ps2.

---

### Post by marmuta on 2009-01-08
Ok, I'm running a single port bond myself now.
```
# cat /etc/network interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
 
auto bond0
iface bond0 inet static
	address 192.168.x.x
	netmask 255.255.255.0
	network 192.168.x.0
	broadcast 192.168.2.255
	gateway 192.168.x.x
        up /sbin/ifenslave bond0 eth0
        down /sbin/ifenslave -d bond0 eth0

```

And the routes are clean:
```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.x.x     0.0.0.0         255.255.255.0   U     0      0        0 bond0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 bond0
0.0.0.0         192.168.x.x     0.0.0.0         UG    100    0        0 bond0

```

The key was "iface eth0 inet manual", because [README.Debian]("file:///usr/share/doc/network-manager/README.Debian") has this to say:
 >  [ifupdown]
  managed=true/false

Unmanaged mode will make NetworkManager not touch any wired/wireless device matching
an interface name configured in /etc/network/interfaces.

Default in Ubuntu is Unmanaged mode, see /etc/NetworkManager/nm-systems-settings.conf.


In short, add these lines to your /etc/network/interfaces and restart. The spurious routes should be gone.
```
auto eth0
iface eth0 inet manual
auto eth1
iface eth1 inet manual


```


> **LordVeovis said:**
> Anyways, as far as jaunty goes tho, you think I should install network-manager 

Networkmanager is already installed by default.
If anything I was suggesting to uninstall it, but you shouldn't have to with the above.

> EDIT: It says I have network-manager installed. I can't run it ... 
nm is a daemon and the only visible thing is the applet in the notification area. You can't run it, all starts automatically.

> find / -iname network-manager
works here with sudo, this too: "sudo find / -iname networkmanager"

---

### Post by LordVeovis on 2009-01-08
> **marmuta said:**
> Ok, I'm running a single port bond myself now.

...

And the routes are clean:

...

The key was "iface eth0 inet manual", because [README.Debian]("file:///usr/share/doc/network-manager/README.Debian") has this to say:
 
Default in Ubuntu is Unmanaged mode, see /etc/NetworkManager/nm-systems-settings.conf.


In short, add these lines to your /etc/network/interfaces and restart. The spurious routes should be gone.
```
auto eth0
iface eth0 inet manual
auto eth1
iface eth1 inet manual


```



Networkmanager is already installed by default.
If anything I was suggesting to uninstall it, but you shouldn't have to with the above.


nm is a daemon and the only visible thing is the applet in the notification area. You can't run it, all starts automatically.


works here with sudo, this too: "sudo find / -iname networkmanager"

Thanks for the info, I tried with a '-' in it, so it didnt find it because of that i think (network-manager)  Just added those lines and will check for updates and reboot soon, if not tonight.  I try to only reboot as required.

---

### Post by LordVeovis on 2009-01-08
Works like a charm, thanks for the post!!

EDIT: Solved.

---

### Post by da mono on 2009-02-09
[LordVeovis]("http://ubuntuforums.org/member.php?u=440282"), what kind of NIC's are you using ???

---

