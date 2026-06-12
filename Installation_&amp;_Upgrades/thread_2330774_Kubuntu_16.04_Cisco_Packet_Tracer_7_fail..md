---
title: "Kubuntu 16.04 Cisco Packet Tracer 7 fail."
date: 2016-07-14
forum: Installation &amp; Upgrades
---

### Post by mccalleyt on 2016-07-14
I have followed a few install pages to help but I get the same error every time I try to run it. 

```
 KDEInit could not launch 'PacketTracer7':
 Could not open library '/usr/lib/x86_64-linux-gnu/libkdeinit5_PacketTracer7'.
 Cannot load library /usr/lib/x86_64-linux-gnu/libkdeinit5_PacketTracer7: (/usr/lib/x86_64-linux-gnu/libkdeinit5_PacketTracer7.so: cannot open shared object file: No such file or directory)


```

I am running Kubuntu 16.04 64bit.

---

### Post by wagnersenger on 2016-09-13
I'm having the same issue in the same SO

---

### Post by mmxals on 2016-10-23
I have 16.04.1 too and my packettracer directory is /opt/pt7 (default = /opt/pt/)

it works for me:

```
$sudo ln -s /opt/pt7/packettracer /usr/local/bin/PacketTracer7

$ ls /usr/local/bin/ -la
[...]
lrwxrwxrwx  1 root root    21 oct 23 17:44 packettracer -> /opt/pt7/packettracer
lrwxrwxrwx  1 root root    21 oct 23 17:53 PacketTracer7 -> /opt/pt7/packettracer
[...]
```

---

### Post by jlamsens on 2017-03-07
Just had that same problem a few minutes ago on Linux Mint KDE 18.

Solved it like this:

sun bin # apt-cache search libkdeinit
pkg-kde-tools - various packaging tools and scripts for KDE Applications

sun bin # apt-get install pkg-kde-tools
...

Now Packettracer starts.

Greets,
Jurgen L.

---

