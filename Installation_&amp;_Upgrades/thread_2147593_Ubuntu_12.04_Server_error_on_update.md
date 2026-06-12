---
title: "Ubuntu 12.04 Server error on update"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by larzeb on 2013-05-22
I am having trouble updating the operating system. I get an error when running [COLOR=#ff0000][FONT=courier new]sudo apt-get update[/FONT][/COLOR]

```
[FONT=courier new]Ign http://us.archive.ubuntu.com precise-backports/universe TranslationIndex[/FONT]
[FONT=courier new]Err http://us.archive.ubuntu.com precise-updates/main Sources[/FONT]
[FONT=courier new]  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.13 80]
...[/FONT]

```

I have included some commands which might help. Any ideas on what might fix this? I am in the US.

Thanks Larry

```
[FONT=courier new]larry@ubuntu:~$ [/FONT][COLOR=#ff0000][FONT=courier new]nslookup ubuntu.com[/FONT][/COLOR]
[FONT=courier new];; connection timed out; no servers could be reached[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]larry@ubuntu:~$ [COLOR=#ff0000]nslookup google.com[/COLOR][/FONT]
[FONT=courier new]Server:        8.8.4.4[/FONT]
[FONT=courier new]Address:    8.8.4.4#53[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]Non-authoritative answer:[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.40[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.32[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.37[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.38[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.39[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.41[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.33[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.36[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.46[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.35[/FONT]
[FONT=courier new]Name:    google.com[/FONT]
[FONT=courier new]Address: 74.125.225.34[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]larry@ubuntu:~$ [COLOR=#ff0000]dig ubuntu.com[/COLOR][/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]; <<>> DiG 9.8.1-P1 <<>> ubuntu.com[/FONT]
[FONT=courier new];; global options: +cmd[/FONT]
[FONT=courier new];; Got answer:[/FONT]
[FONT=courier new];; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51796[/FONT]
[FONT=courier new];; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; QUESTION SECTION:[/FONT]
[FONT=courier new];ubuntu.com.            IN    A[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; ANSWER SECTION:[/FONT]
[FONT=courier new]ubuntu.com.        391    IN    A    91.189.94.156[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new];; Query time: 1758 msec[/FONT]
[FONT=courier new];; SERVER: 8.8.4.4#53(8.8.4.4)[/FONT]
[FONT=courier new];; WHEN: Wed May 22 08:01:43 2013[/FONT]
[FONT=courier new];; MSG SIZE  rcvd: 44[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]larry@ubuntu:~$ [COLOR=#ff0000]ifconfig[/COLOR][/FONT]
[FONT=courier new]eth1      Link encap:Ethernet  HWaddr 00:1b:21:36:23:2e  [/FONT]
[FONT=courier new]          inet addr:192.168.10.24  Bcast:192.168.10.255  Mask:255.255.255.0[/FONT]
[FONT=courier new]          inet6 addr: fe80::21b:21ff:fe36:232e/64 Scope:Link[/FONT]
[FONT=courier new]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:13756 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:12487 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:1000 [/FONT]
[FONT=courier new]          RX bytes:6735920 (6.7 MB)  TX bytes:2951364 (2.9 MB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]lo        Link encap:Local Loopback  [/FONT]
[FONT=courier new]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
[FONT=courier new]          inet6 addr: ::1/128 Scope:Host[/FONT]
[FONT=courier new]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
[FONT=courier new]          RX packets:81 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:0 [/FONT]
[FONT=courier new]          RX bytes:5670 (5.6 KB)  TX bytes:5670 (5.6 KB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  [/FONT]
[FONT=courier new]          inet addr:10.16.0.14  P-t-P:10.16.0.13  Mask:255.255.255.255[/FONT]
[FONT=courier new]          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1[/FONT]
[FONT=courier new]          RX packets:7380 errors:0 dropped:0 overruns:0 frame:0[/FONT]
[FONT=courier new]          TX packets:6854 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
[FONT=courier new]          collisions:0 txqueuelen:100 [/FONT]
[FONT=courier new]          RX bytes:4645590 (4.6 MB)  TX bytes:745975 (745.9 KB)[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]larry@ubuntu:~$ [COLOR=#ff0000]route -n[/COLOR][/FONT]
[FONT=courier new]Kernel IP routing table[/FONT]
[FONT=courier new]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT]
[FONT=courier new]0.0.0.0         10.16.0.13      128.0.0.0       UG    0      0        0 tun0[/FONT]
[FONT=courier new]0.0.0.0         192.168.10.254  0.0.0.0         UG    100    0        0 eth1[/FONT]
[FONT=courier new]10.16.0.1       10.16.0.13      255.255.255.255 UGH   0      0        0 tun0[/FONT]
[FONT=courier new]10.16.0.13      0.0.0.0         255.255.255.255 UH    0      0        0 tun0[/FONT]
[FONT=courier new]128.0.0.0       10.16.0.13      128.0.0.0       UG    0      0        0 tun0[/FONT]
[FONT=courier new]184.105.235.195 192.168.10.254  255.255.255.255 UGH   0      0        0 eth1[/FONT]
[FONT=courier new]192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1[/FONT]





```

---

### Post by dino99 on 2013-05-22
its an issue with the us.archive server; you cant do anything, except using an other server's archive (remove "us" to get the "main" server instead)

---

### Post by larzeb on 2013-05-22
Thanks, Dino, I changed "us" to "main" in /etc/apt/sources.list and that did the trick.

---

