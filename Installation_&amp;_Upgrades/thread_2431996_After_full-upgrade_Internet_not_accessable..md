---
title: "After full-upgrade Internet not accessable."
date: 2019-11-25
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-11-25
I ran a full_upgrade on my 16.04 machine and while the local network works, 
I can login from a desktop using Putty, but I can't ssh from the machine.

I cannot access the Internet.

```
ping 8.8.8.8 
```
fails

Network-manager says there is > "No valid active connections found!

```
# ifconfig -a
enp1s0    Link encap:Ethernet  HWaddr 70:85:c2:68:f6:fe
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7285:c2ff:fe68:f6fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37921 errors:0 dropped:10626 overruns:0 frame:0
          TX packets:11134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19949614 (19.9 MB)  TX bytes:2597973 (2.5 MB)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:29058 (29.0 KB)  TX bytes:29058 (29.0 KB)
```

It worked just fine Friday.

---

### Post by TheFu on 2019-11-25
That IP address seems like it should be for the router.

Did you check the router?
Ethernet cable?
Switch port/
routing table?

---

### Post by rsteinmetz70112 on 2019-11-26
The router is 192.168.1.254 - Blame ATT

> Did you check the router?
Router works for all other computers on the network.
> Ethernet cable?
Swapped cables.
> Switch port/
Swapped switches. I have a large switch I normally use but the router has a small switch in it. 
> routing table? 
No

I'm beginning to suspect a hardware problem on the Motherboard.
I think I'll try a live session and see if that works.
Unfortunately that will have to wait until after Thanksgiving, I'll be traveling.

I do have remote access via ssh.

---

### Post by TheFu on 2019-11-26
> **rsteinmetz70112 said:**
>  
No

I'm beginning to suspect a hardware problem on the Motherboard.
I think I'll try a live session and see if that works.
Unfortunately that will have to wait until after Thanksgiving, I'll be traveling.

I do have remote access via ssh.

I take it remote access is through a different machine on the LAN?

$ route -n?
does it look correct?  I hate the **ip r** output. Too ugly.

Just for completeness - is this network-manager or netplan AND static or DHCP?

I had something similar with 16.04, but only inside a virtual machine and only for 1 virtual machine connected to the same bridge. There are about 8 other VMs on the same bridge.  Never figured out the issue. It fixed itself within a few days without rebooting the switches, routers, or host machine.  Rebooting the impacted VM didn't help.  A few months later, the same issue happened on the same VM and again, a few days later it self-fixed.  I moved that VM to a different VM host and haven't see the issue in over a year.  There was nothing different about the problem VM. I use ansible to configure networking for all of them, so besides the IP, it was configured the same as the other VMs for networking.

In short - I've felt THIS pain too and I believe you.

---

### Post by rsteinmetz70112 on 2019-11-26
> **TheFu said:**
> I take it remote access is through a different machine on the LAN?[\quote]
Not exactly there is a machine on the lan which does address translation and directs the connection is directly to the machine in question. I can get in I just can't get out.

> $ route -n?
does it look correct?  I hate the **ip r** output. Too ugly.

```
~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp1s0
```

[QUOTE]Just for completeness - is this network-manager or netplan AND static or DHCP?

It is static through /etc/network/interfaces

> I had something similar with 16.04, but only inside a virtual machine and only for 1 virtual machine connected to the same bridge. There are about 8 other VMs on the same bridge.  Never figured out the issue. It fixed itself within a few days without rebooting the switches, routers, or host machine.  Rebooting the impacted VM didn't help.  A few months later, the same issue happened on the same VM and again, a few days later it self-fixed.  I moved that VM to a different VM host and haven't see the issue in over a year.  There was nothing different about the problem VM. I use ansible to configure networking for all of them, so besides the IP, it was configured the same as the other VMs for networking.

In short - I've felt THIS pain too and I believe you.

I've since had another 19.04 machine do almost the same thing. I believe it was somehow caused by a routine upgrade. I have discovered that the resolver wasn't working quire right and added nameserver lines to /etc/resolv.conf. That fixed the problem. Now I just have to convince the machine not to rewire /etc/resolve.conf or at least put the right stuff in it.

---

### Post by rsteinmetz70112 on 2019-11-27
I'm going to make this solved. I still havn't figured out how /etc/resolv.conf got changed. I suspect a routine upgrade.

---

