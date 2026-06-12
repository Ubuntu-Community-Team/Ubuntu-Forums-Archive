---
title: "FakeRaid Installation - &quot;dmraid&quot; cannot be installed"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Dinglekürbis on 2008-05-06
Hi,

I'm just trying to install Hardy Heron. But to activate my Raid0 Stripe (FakeRaid), I have to install "dmraid". So I do as the [FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) tells me to do.

But my Ubuntu (booted from LiveCD) has a problem with "dmraid".

I tried several times and different methods, but all I get is this:

```
ubuntu@ubuntu:~$ sudo apt-get install dmraid
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Reading state information... Fertig
Die folgenden NEUEN Pakete werden installiert:
  dmraid
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen 176kB Archive geholt werden.
After this operation, 614kB of additional disk space will be used.
Hole:1 http://archive.ubuntu.com hardy/universe dmraid 1.0.0.rc14-0ubuntu3 [176kB]
Es wurden 176kB in 14s geholt (12,5kB/s)                                                                                                                                                               
Wähle vormals abgewähltes Paket dmraid.
(Lese Datenbank ... 98223 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke dmraid (aus .../dmraid_1.0.0.rc14-0ubuntu3_i386.deb) ...
Richte dmraid ein (1.0.0.rc14-0ubuntu3) ...
 * Setting up DMRAID devices...                                                                                                                                                                         *** glibc detected *** /sbin/dmraid: malloc(): memory corruption: 0x08070778 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d93356]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb7d94cad]
/sbin/dmraid[0x8054ce7]
/sbin/dmraid(alloc_private+0x22)[0x8050a02]
/sbin/dmraid(alloc_private_and_read+0x3f)[0x805113f]
/sbin/dmraid(read_raid_dev+0x1ce)[0x805136e]
/sbin/dmraid[0x805cbbd]
/sbin/dmraid[0x8052fb2]
/sbin/dmraid(discover_raid_devices+0x109)[0x8053489]
/sbin/dmraid(perform+0x1e5)[0x804b7a5]
/sbin/dmraid(main+0xa0)[0x804b130]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d3d450]
/sbin/dmraid[0x804b021]
======= Memory map: ========
08048000-0806d000 r-xp 00000000 00:11 57967      /cow/sbin/dmraid
0806d000-0806e000 rw-p 00025000 00:11 57967      /cow/sbin/dmraid
0806e000-08090000 rw-p 0806e000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0 
b7c21000-b7d00000 ---p b7c21000 00:00 0 
b7d17000-b7d21000 r-xp 00000000 07:00 107578     /rofs/lib/libgcc_s.so.1
b7d21000-b7d22000 rw-p 0000a000 07:00 107578     /rofs/lib/libgcc_s.so.1
b7d22000-b7d23000 rw-p b7d22000 00:00 0 
b7d23000-b7d25000 r-xp 00000000 07:00 107723     /rofs/lib/tls/i686/cmov/libdl-2.7.so
b7d25000-b7d27000 rw-p 00001000 07:00 107723     /rofs/lib/tls/i686/cmov/libdl-2.7.so
b7d27000-b7e70000 r-xp 00000000 07:00 107720     /rofs/lib/tls/i686/cmov/libc-2.7.so
b7e70000-b7e71000 r--p 00149000 07:00 107720     /rofs/lib/tls/i686/cmov/libc-2.7.so
b7e71000-b7e73000 rw-p 0014a000 07:00 107720     /rofs/lib/tls/i686/cmov/libc-2.7.so
b7e73000-b7e76000 rw-p b7e73000 00:00 0 
b7e76000-b7ea9000 r-xp 00000000 07:00 107634     /rofs/lib/libsepol.so.1
b7ea9000-b7eaa000 rw-p 00032000 07:00 107634     /rofs/lib/libsepol.so.1
b7eaa000-b7eab000 rw-p b7eaa000 00:00 0 
b7eab000-b7ec2000 r-xp 00000000 07:00 107633     /rofs/lib/libselinux.so.1
b7ec2000-b7ec4000 rw-p 00016000 07:00 107633     /rofs/lib/libselinux.so.1
b7ec4000-b7ed8000 r-xp 00000000 07:00 107577     /rofs/lib/libdevmapper.so.1.02.1
b7ed8000-b7eda000 rw-p 00013000 07:00 107577     /rofs/lib/libdevmapper.so.1.02.1
b7ee5000-b7ee7000 rw-p b7ee5000 00:00 0 
b7ee7000-b7ee8000 r-xp b7ee7000 00:00 0          [vdso]
b7ee8000-b7f02000 r-xp 00000000 07:00 107532     /rofs/lib/ld-2.7.so
b7f02000-b7f04000 rw-p 00019000 07:00 107532     /rofs/lib/ld-2.7.so
bfa6d000-bfa82000 rw-p bffeb000 00:00 0          [stack]
/etc/init.d/dmraid: line 13:  9411 Aborted                 /sbin/dmraid --activate yes --ignorelocking > /dev/null 2>&1
invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: Fehler beim Bearbeiten von dmraid (--configure):
 Unterprozess post-installation script gab den Fehlerwert 134 zurück
Fehler traten auf beim Bearbeiten von:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ 
```

Does anyone know what the problem is? I consider myself an experienced computer user (programmer as well), but I cannot even find Threads within this board dealing with installation problems of "dmraid".

Thanks for any help. :)

---

