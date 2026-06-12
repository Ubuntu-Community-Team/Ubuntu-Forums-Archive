---
title: "Network loss during routine upgrade"
date: 2022-06-26
forum: Installation &amp; Upgrades
---

### Post by Bo Rosén on 2022-06-26
A couple of days ago I did a normal update of 22.04, but during the process my Internet went down. Now I can't go online anymore. I have a wired connection, and I get an IP from my router, but I can't get online. I dual boot and it works in Win10 (and a Ubuntu live disk).

Any suggestions?

Edit: Should probably be moved to the correct subforum

---

### Post by grahammechanical on 2022-06-26
There is something you could try. It may or may not work. At the Grub boot menu select Advanced Options for Ubuntu and select a Linux kernel with a recovery mode. That shpuld load to a recovery menu. At the recovery menu select Network. That will attempt to connect to the router/hub. If the hub is connected to the internet service provider (ISP) then you should have internet access.

When back at the recovery menu select Root shell prompt and then run

```
apt update
apt upgrade
```

Try to finish off the update/upgrade that was interrupted. To exit Root shell prompt type "exit." When back at the recovery menu select Resume. That will load to the desktop using a low resolution open source video driver. A reboot will load Ubuntu with the normal video driver.

The update that was interrupted may have included updates to various network utilities.

Regards

---

### Post by Bo Rosén on 2022-06-26
Thanks for the reply, 
I just get errors that it failed to look up the repos.

---

### Post by TheFu on 2022-06-26
Network troubleshooting: [https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
Follow those steps, in order, run the commands, save both the command AND the output to a text file, then move that text file to a computer where you can post them back here, wrapped in forum 'code tags', so the output is readable.

Sometimes, network issues are just DNS issues.  To non-technical people, there isn't much difference, but there is a huge difference.

---

### Post by Bo Rosén on 2022-06-26
Net-tools wasn't installed, so I couldn't run the route command.It's a wired connection btw. Could I install it from a live-disk?

```

brosen@Delirium:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 04:92:26:5b:7c:b1 brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
    inet 192.168.0.183/24 brd 192.168.0.255 scope global dynamic noprefixroute eno1
       valid_lft 6922sec preferred_lft 6922sec
    inet6 fe80::be86:3f9e:cbcf:b297/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: pvpnroutintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether de:33:5d:43:92:90 brd ff:ff:ff:ff:ff:ff
    inet 100.85.0.1/24 brd 100.85.0.255 scope global noprefixroute pvpnroutintrf0
       valid_lft forever preferred_lft forever
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::20b0:b37c:8022:c16/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: pvpnksintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether ae:5f:ad:fe:c9:85 brd ff:ff:ff:ff:ff:ff
    inet 100.85.0.1/24 brd 100.85.0.255 scope global noprefixroute pvpnksintrf0
       valid_lft forever preferred_lft forever
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::efd2:3054:2ed9:46a1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
5: ipv6leakintrf0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether 06:14:2d:42:a4:78 brd ff:ff:ff:ff:ff:ff
    inet6 fdeb:446c:912d:8da::/64 scope global noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::f055:bcde:6592:c68e/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
       
net-tools isn't installed, so no route command

brosen@Delirium:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.245 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.345 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.262 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=0.325 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=0.270 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=0.293 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=0.264 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=0.278 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=0.252 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=0.265 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=0.259 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=0.254 ms
64 bytes from 192.168.0.1: icmp_seq=13 ttl=64 time=0.251 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=0.266 ms
64 bytes from 192.168.0.1: icmp_seq=15 ttl=64 time=0.258 ms

ping google.com
ping: google.com: Name Look up failed temporarily (I have everthing in Swedish, hope the translation makes sense)

brosen@Delirium:~$ sudo dmesg |grep eth [0-9]
grep: [0-9]: Filen eller katalogen finns inte (Transl. The file or folder does not exist)

brosen@Delirium:~$ sudo lshw -C network
  *-network                 
       beskrivning: Ethernet interface
       produkt: Ethernet Connection (7) I219-V
       tillverkare: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logiskt namn: eno1
       version: 10
       serienummer: 04:92:26:5b:7c:b1
       storlek: 1Gbit/s
       kapacitet: 1Gbit/s
       bredd: 32 bits
       klocka: 33MHz
       förmågor: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       konfiguration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.15.0-40-generic duplex=full firmware=0.4-4 ip=192.168.0.183 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resurser: irq:129 memory:a4300000-a431ffff


rosen@Delirium:~$ more /etc/resolv.conf 
# This is /run/systemd/resolve/stub-resolv.conf managed by man:systemd-resolved(
8).
# Do not edit.
#
# This file might be symlinked as /etc/resolv.conf. If you're looking at
# /etc/resolv.conf and seeing this text, you have followed the symlink.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs should typically not access this file directly, but only
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a
# different way, replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
options edns0 trust-ad
search .


```

---

### Post by grahammechanical on 2022-06-26
> I just get errors that it failed to look up the repos.

Does this mean that you now get internet access? Can you now get online? Not accessing the repositories is a different problem from your original problem where you said that you could not get online.

Please provide the output from this command

```
sudo apt update
```

Regards

---

### Post by TheFu on 2022-06-26
a) turn off the VPN.
b) looks like the system has a DNS problem.
c)** ip route | column -t**  is the same as the route -n command, mostly.

Appears the system is using systemd-resolved.  Try restarting that daemon.

---

### Post by Bo Rosén on 2022-06-26
sudo apt-get update

```

brosen@Delirium:~$ sudo apt update
[sudo] lösenord för brosen: 
Läser paketlistor&#8230; Färdig
E: Could not get lock /var/lib/apt/lists/lock. It is held by process 1573 (packagekitd)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Kunde inte låsa katalogen /var/lib/apt/lists/

```

While I have a VPN, I haven't activated it. Is it running anyway, somehow?
ip route
```


brosen@Delirium:~$ ip route | column -t
0.0.0.0/1          dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
default            via  100.85.0.1      dev    pvpnksintrf0  proto   static  metric  98                     
default            via  192.168.0.1     dev    eno1          proto   dhcp    metric  100                    
100.85.0.0/24      dev  pvpnroutintrf0  proto  kernel        scope   link    src     100.85.0.1     metric  97
100.85.0.0/24      dev  pvpnksintrf0    proto  kernel        scope   link    src     100.85.0.1     metric  98
128.0.0.0/5        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
136.0.0.0/7        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.0.0.0/9        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.128.0.0/10     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.192.0.0/14     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.196.0.0/15     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.198.0.0/16     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.0.0/19     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.32.0/20    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.48.0/22    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.52.0/23    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.54.0/24    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.0/27    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.32      dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.34/31   dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.36/30   dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.40/29   dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.48/28   dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.64/26   dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.55.128/25  dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.56.0/21    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.64.0/18    dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.199.128.0/17   dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.200.0.0/13     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.208.0.0/12     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
138.224.0.0/11     dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
139.0.0.0/8        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
140.0.0.0/6        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
144.0.0.0/4        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
160.0.0.0/3        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
169.254.0.0/16     dev  pvpnroutintrf0  scope  link          metric  1000                                   
192.0.0.0/2        dev  pvpnroutintrf0  proto  static        scope   link    metric  97                     
192.168.0.0/24     dev  eno1            proto  kernel        scope   link    src     192.168.0.183  metric  100

```

I'm starting to think a new install would be easiest, I tried but I get a warning when installing that the system doesn't have a uefi partition, as far as I understand it does. I chickened out. Things have changed so much since the last time I had to mess with partitions that I'm very nervous about ending up with a bricked machine.

I'm truly grateful for you guys trying to help, though.

---

### Post by Bo Rosén on 2022-06-26
> **grahammechanical said:**
> Does this mean that you now get internet access


I can reach my router, but nothing beyond that

---

### Post by grahammechanical on 2022-06-26
> E: Could not get lock /var/lib/apt/lists/lock. It is held by process 1573 (packagekitd)

That is a separate problem apart from not being able to connect to the internet. It is caused by the original update/grade not finishing. When we update the lists file is locked to prevent another update utility from trying to update. It is a safety feature.

You said that you can get an internet connection from Windows and the Ubuntu live session. That proves that your router is connecting to the ISP. I suggest that you open System Settings>Network from the live session or from Windows and make a note of the network settings and then from the installed Ubuntu enter the same settings in the Network utility.

Regards

---

### Post by TheFu on 2022-06-26
Disable the VPN. That's the current problem.  Doing that might fix the issue.  It is definitely polluting the routing table.

---

### Post by Bo Rosén on 2022-06-27
> **TheFu said:**
> Disable the VPN. That's the current problem.  Doing that might fix the issue.  It is definitely polluting the routing table.

That fixed it!  Writing this on the affected computer. 
Thank you both, I was about ready to give up. Now I won't have to spend my last day of vacation tearing my hair out worrying about this. :D

---

