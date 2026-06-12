---
title: "[B]Can Anyone Please Help ?[/B]"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by philipsone on 2008-05-08
**So Nearly There...A Linux solution for me and an old machine.**

Installed Ubuntu on old notebook.

Network Connection works. But not the Internet Connection.

Can anyone please help me to get the internet connected?

Thanks.

---

### Post by AlbertTatlocksCap on 2008-05-08
Check the DNS setting in your network configuration

I think it should point to your router

Hope this helps

---

### Post by philipsone on 2008-05-08
Other machine on the same router connects to internet.

---

### Post by philipsone on 2008-05-08
And the notebook can access router admin.

---

### Post by christianxxx on 2008-05-08
Could there be something in the router setup to disallow internet access from that computer?

---

### Post by brigux on 2008-05-08
ifconfig -a
netstat -na
cat /etc/resolv.conf

?

---

### Post by Em-Buntu on 2008-05-08
Ensure that DHCP is enabled in your network setup.

---

### Post by philipsone on 2008-05-08
Thanks. It is.

---

### Post by philipsone on 2008-05-08
ian@MonOldTosh:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:39:12:56:3B
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe12:563b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148180 (144.7 KiB)  TX bytes:60811 (59.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ian@MonOldTosh:~$ netstat -na
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:43465         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:52927         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:43465         127.0.0.1:47683         ESTABLISHED
tcp        0      0 127.0.0.1:47683         127.0.0.1:43465         ESTABLISHED
udp        0      0 0.0.0.0:68              0.0.0.0:*
raw        0      0 0.0.0.0:1               0.0.0.0:*               7
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  3      [ ]         DGRAM                    13323    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     10655    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     12245    /tmp/mapping-ian
unix  2      [ ]         DGRAM                    4964     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     10881    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     10959    @/tmp/hald-runner/dbus-tBOGJeYr4Q
unix  2      [ ACC ]     STREAM     LISTENING     11800    @/tmp/dbus-4iKcgVtFAtunix  2      [ ]         DGRAM                    10967    @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     11420    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     9632     /var/run/acpid.socketunix  2      [ ACC ]     STREAM     LISTENING     10935    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     10723    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11795    /tmp/ssh-EKrbFZ4857/agent.4857
unix  2      [ ACC ]     STREAM     LISTENING     11819    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  2      [ ACC ]     STREAM     LISTENING     11830    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  2      [ ACC ]     STREAM     LISTENING     10958    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  2      [ ACC ]     STREAM     LISTENING     11853    /tmp/.ICE-unix/4857
unix  2      [ ACC ]     STREAM     LISTENING     11863    /tmp/keyring-nL3eUd/socket
unix  2      [ ACC ]     STREAM     LISTENING     11876    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  2      [ ACC ]     STREAM     LISTENING     11905    /tmp/.esd-1000/socketunix  2      [ ACC ]     STREAM     LISTENING     11916    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  2      [ ACC ]     STREAM     LISTENING     11949    /tmp/orbit-ian/linc-133b-0-43c9cb9f27a0d
unix  2      [ ACC ]     STREAM     LISTENING     11978    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  2      [ ACC ]     STREAM     LISTENING     12007    /tmp/orbit-ian/linc-1345-0-4546456775bf9
unix  2      [ ACC ]     STREAM     LISTENING     12017    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  2      [ ACC ]     STREAM     LISTENING     12057    /tmp/orbit-ian/linc-134c-0-3345e5c77184c
unix  2      [ ACC ]     STREAM     LISTENING     12102    /tmp/orbit-ian/linc-134e-0-3345e5c62660b
unix  2      [ ACC ]     STREAM     LISTENING     12120    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  2      [ ACC ]     STREAM     LISTENING     12142    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  2      [ ACC ]     STREAM     LISTENING     12154    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  2      [ ACC ]     STREAM     LISTENING     12273    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  2      [ ACC ]     STREAM     LISTENING     12290    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  2      [ ACC ]     STREAM     LISTENING     12395    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  2      [ ACC ]     STREAM     LISTENING     12455    /tmp/orbit-ian/linc-1391-0-4ee32b326fac
unix  2      [ ACC ]     STREAM     LISTENING     12569    /tmp/orbit-ian/linc-13b7-0-5eca89d0a330b
unix  2      [ ACC ]     STREAM     LISTENING     20963    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20976
unix  3      [ ]         STREAM     CONNECTED     20975
unix  3      [ ]         STREAM     CONNECTED     20973    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     20972
unix  3      [ ]         STREAM     CONNECTED     20970    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20969
unix  3      [ ]         STREAM     CONNECTED     20968    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     20967
unix  3      [ ]         STREAM     CONNECTED     20966    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20965
unix  3      [ ]         STREAM     CONNECTED     20962    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     20961
unix  3      [ ]         STREAM     CONNECTED     20958    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     20957
unix  3      [ ]         STREAM     CONNECTED     20953    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20952
unix  2      [ ]         DGRAM                    16362
unix  3      [ ]         STREAM     CONNECTED     12572    /tmp/orbit-ian/linc-13b7-0-5eca89d0a330b
unix  3      [ ]         STREAM     CONNECTED     12571
unix  3      [ ]         STREAM     CONNECTED     12568    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12567
unix  3      [ ]         STREAM     CONNECTED     12553    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12552
unix  3      [ ]         STREAM     CONNECTED     12462    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12461
unix  3      [ ]         STREAM     CONNECTED     12460    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12459
unix  3      [ ]         STREAM     CONNECTED     12458    /tmp/orbit-ian/linc-1391-0-4ee32b326fac
unix  3      [ ]         STREAM     CONNECTED     12457
unix  3      [ ]         STREAM     CONNECTED     12454    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12453
unix  3      [ ]         STREAM     CONNECTED     12449    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12448
unix  3      [ ]         STREAM     CONNECTED     12433    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12432
unix  3      [ ]         STREAM     CONNECTED     12431    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12430
unix  3      [ ]         STREAM     CONNECTED     12429    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12428
unix  3      [ ]         STREAM     CONNECTED     12423    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12422
unix  3      [ ]         STREAM     CONNECTED     12419    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12418
unix  3      [ ]         STREAM     CONNECTED     12417    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12416
unix  3      [ ]         STREAM     CONNECTED     12407    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12406
unix  3      [ ]         STREAM     CONNECTED     12404    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     12403
unix  3      [ ]         STREAM     CONNECTED     12402    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12401
unix  3      [ ]         STREAM     CONNECTED     12400    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12399
unix  3      [ ]         STREAM     CONNECTED     12398    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12397
unix  3      [ ]         STREAM     CONNECTED     12394    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12393
unix  3      [ ]         STREAM     CONNECTED     12389    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12388
unix  3      [ ]         STREAM     CONNECTED     12324    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     12323
unix  3      [ ]         STREAM     CONNECTED     12322    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12321
unix  3      [ ]         STREAM     CONNECTED     12319    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12318
unix  3      [ ]         STREAM     CONNECTED     12317    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12316
unix  3      [ ]         STREAM     CONNECTED     12310    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12309
unix  3      [ ]         STREAM     CONNECTED     12307    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12306
unix  3      [ ]         STREAM     CONNECTED     12297    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12296
unix  3      [ ]         STREAM     CONNECTED     12295    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12294
unix  3      [ ]         STREAM     CONNECTED     12293    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12292
unix  3      [ ]         STREAM     CONNECTED     12289    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12288
unix  3      [ ]         STREAM     CONNECTED     12284    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12283
unix  3      [ ]         STREAM     CONNECTED     12280    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12279
unix  3      [ ]         STREAM     CONNECTED     12278    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12277
unix  3      [ ]         STREAM     CONNECTED     12276    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12275
unix  3      [ ]         STREAM     CONNECTED     12272    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12271
unix  3      [ ]         STREAM     CONNECTED     12267    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12266
unix  3      [ ]         STREAM     CONNECTED     12249    /tmp/mapping-ian
unix  3      [ ]         STREAM     CONNECTED     12241
unix  3      [ ]         STREAM     CONNECTED     12210    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12209
unix  3      [ ]         STREAM     CONNECTED     12208    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12207
unix  3      [ ]         STREAM     CONNECTED     12200    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12199
unix  3      [ ]         STREAM     CONNECTED     12196    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12195
unix  3      [ ]         STREAM     CONNECTED     12194    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12193
unix  3      [ ]         STREAM     CONNECTED     12186    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12185
unix  3      [ ]         STREAM     CONNECTED     12184    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12183
unix  3      [ ]         STREAM     CONNECTED     12182    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12180
unix  3      [ ]         STREAM     CONNECTED     12181    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12176
unix  3      [ ]         STREAM     CONNECTED     12173    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12172
unix  3      [ ]         STREAM     CONNECTED     12171    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12170
unix  3      [ ]         STREAM     CONNECTED     12163    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     12162
unix  3      [ ]         STREAM     CONNECTED     12161    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  3      [ ]         STREAM     CONNECTED     12160
unix  3      [ ]         STREAM     CONNECTED     12159    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12158
unix  3      [ ]         STREAM     CONNECTED     12157    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  3      [ ]         STREAM     CONNECTED     12156
unix  3      [ ]         STREAM     CONNECTED     12153    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12152
unix  3      [ ]         STREAM     CONNECTED     12149    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12148
unix  3      [ ]         STREAM     CONNECTED     12147    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12146
unix  3      [ ]         STREAM     CONNECTED     12145    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12144
unix  3      [ ]         STREAM     CONNECTED     12138    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12137
unix  3      [ ]         STREAM     CONNECTED     12134    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12133
unix  3      [ ]         STREAM     CONNECTED     12127    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12126
unix  3      [ ]         STREAM     CONNECTED     12125    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12124
unix  3      [ ]         STREAM     CONNECTED     12123    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12122
unix  3      [ ]         STREAM     CONNECTED     12119    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12118
unix  3      [ ]         STREAM     CONNECTED     12114    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12113
unix  3      [ ]         STREAM     CONNECTED     12110    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12109
unix  3      [ ]         STREAM     CONNECTED     12108    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12107
unix  2      [ ]         DGRAM                    12106
unix  3      [ ]         STREAM     CONNECTED     12105    /tmp/orbit-ian/linc-134e-0-3345e5c62660b
unix  3      [ ]         STREAM     CONNECTED     12104
unix  3      [ ]         STREAM     CONNECTED     12101    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12100
unix  3      [ ]         STREAM     CONNECTED     12094    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12093
unix  3      [ ]         STREAM     CONNECTED     12086    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12085
unix  3      [ ]         STREAM     CONNECTED     12082    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12074
unix  3      [ ]         STREAM     CONNECTED     12073    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12072
unix  3      [ ]         STREAM     CONNECTED     12067    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12066
unix  3      [ ]         STREAM     CONNECTED     12062    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12061
unix  3      [ ]         STREAM     CONNECTED     12060    /tmp/orbit-ian/linc-134c-0-3345e5c77184c
unix  3      [ ]         STREAM     CONNECTED     12059
unix  3      [ ]         STREAM     CONNECTED     12056    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12055
unix  3      [ ]         STREAM     CONNECTED     12052    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12049
unix  3      [ ]         STREAM     CONNECTED     12045    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12044
unix  3      [ ]         STREAM     CONNECTED     12031    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12030
unix  3      [ ]         STREAM     CONNECTED     12026    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12025
unix  3      [ ]         STREAM     CONNECTED     12023    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12022
unix  3      [ ]         STREAM     CONNECTED     12020    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12019
unix  3      [ ]         STREAM     CONNECTED     12016    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12015
unix  3      [ ]         STREAM     CONNECTED     12012    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12011
unix  3      [ ]         STREAM     CONNECTED     12010    /tmp/orbit-ian/linc-1345-0-4546456775bf9
unix  3      [ ]         STREAM     CONNECTED     12009
unix  3      [ ]         STREAM     CONNECTED     12006    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12005
unix  3      [ ]         STREAM     CONNECTED     12002    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12001
unix  3      [ ]         STREAM     CONNECTED     11997    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11996
unix  3      [ ]         STREAM     CONNECTED     11990    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11989
unix  3      [ ]         STREAM     CONNECTED     11985    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     11984
unix  3      [ ]         STREAM     CONNECTED     11983    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     11982
unix  3      [ ]         STREAM     CONNECTED     11981    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     11980
unix  3      [ ]         STREAM     CONNECTED     11977    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11976
unix  3      [ ]         STREAM     CONNECTED     11973    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     11970
unix  3      [ ]         STREAM     CONNECTED     11964    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11963
unix  3      [ ]         STREAM     CONNECTED     11956    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     11955
unix  3      [ ]         STREAM     CONNECTED     11954    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11953
unix  3      [ ]         STREAM     CONNECTED     11952    /tmp/orbit-ian/linc-133b-0-43c9cb9f27a0d
unix  3      [ ]         STREAM     CONNECTED     11951
unix  3      [ ]         STREAM     CONNECTED     11948    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11947
unix  3      [ ]         STREAM     CONNECTED     11919    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     11918
unix  3      [ ]         STREAM     CONNECTED     11915    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11914
unix  3      [ ]         STREAM     CONNECTED     11912    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     11910
unix  2      [ ]         STREAM                   11904
unix  3      [ ]         STREAM     CONNECTED     11894    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11893
unix  3      [ ]         STREAM     CONNECTED     11882    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  3      [ ]         STREAM     CONNECTED     11881
unix  3      [ ]         STREAM     CONNECTED     11880    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     11879
unix  3      [ ]         STREAM     CONNECTED     11834    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  3      [ ]         STREAM     CONNECTED     11833
unix  3      [ ]         STREAM     CONNECTED     11832    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11829
unix  2      [ ]         DGRAM                    11814
unix  3      [ ]         STREAM     CONNECTED     11808    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11807
unix  3      [ ]         STREAM     CONNECTED     11804    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11803
unix  3      [ ]         STREAM     CONNECTED     11802
unix  3      [ ]         STREAM     CONNECTED     11801
unix  3      [ ]         STREAM     CONNECTED     11417    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11412
unix  2      [ ]         DGRAM                    11409
unix  2      [ ]         DGRAM                    11390
unix  3      [ ]         STREAM     CONNECTED     11281    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11280
unix  3      [ ]         STREAM     CONNECTED     11263    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11261
unix  3      [ ]         STREAM     CONNECTED     11262    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11255
unix  3      [ ]         STREAM     CONNECTED     11211    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11206
unix  3      [ ]         STREAM     CONNECTED     11085    /var/run/acpid.socketunix  3      [ ]         STREAM     CONNECTED     11084
unix  3      [ ]         STREAM     CONNECTED     11089    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11079
unix  3      [ ]         STREAM     CONNECTED     10962    @/tmp/hald-runner/dbus-tBOGJeYr4Q
unix  3      [ ]         STREAM     CONNECTED     10961
unix  3      [ ]         STREAM     CONNECTED     10938
unix  3      [ ]         STREAM     CONNECTED     10937
unix  2      [ ]         DGRAM                    10758
unix  4      [ ]         STREAM     CONNECTED     10892    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10732
unix  2      [ ]         DGRAM                    9833
ian@MonOldTosh:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
ian@MonOldTosh:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.

---

### Post by brigux on 2008-05-08
sorry I meant netstat -ra. I wanted to see your rooting table not your port table.

---

### Post by brigux on 2008-05-08
> **philipsone said:**
> 
ian@MonOldTosh:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
ian@MonOldTosh:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.

Looks like everything's working fine.. Can you describe what's happening when you type in [www.google.com](www.google.com) in a browser.
Alternatvely what's happening when you type:
```
wget www.google.com 
```
from the command line?

---

### Post by philipsone on 2008-05-08
ian@MonOldTosh:~$ netstat -ra
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
default         mygateway1.ar7  0.0.0.0         UG        0 0          0 eth0
ian@MonOldTosh:~$

---

### Post by philipsone on 2008-05-08
> **brigux said:**
> Looks like everything's working fine.. Can you describe what's happening when you type in [www.google.com](www.google.com) in a browser.
Alternatvely what's happening when you type:
```
wget www.google.com 
```
from the command line?
ian@MonOldTosh:~$ wget [www.google.com](www.google.com)
--05:19:46--   [http://www.google.com/](http://www.google.com/)
             => 'index.html'
Resolving [www.google.com](www.google.com)...  1.0.0.0
Connecting to [www.google.com|1.0.0.0|:80](www.google.com|1.0.0.0|:80)... failed:  No route to host.
ian@MonOldTosh:~$

---

### Post by brigux on 2008-05-08
fun...

can you 
```
wget 72.14.207.99
```
```
traceroute 72.14.207.99
```

---

### Post by philipsone on 2008-05-08
> **brigux said:**
> fun...

can you 
```
wget 72.14.207.99
```
```
traceroute 72.14.207.99
```

ian@MonOldTosh:~$ wget 72.14.207.99
--06:26:43--  [http://72.14.207.99/](http://72.14.207.99/)
           => `index.html'
Connecting to 72.14.207.99:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                                 ] 6,685         33.30K/s

06:26:44 (33.14 KB/s) - `index.html' saved [6685]

ian@MonOldTosh:~$ traceroute 72.14.207.99
bash: traceroute: command not found
ian@MonOldTosh:~$

---

### Post by rickh57 on 2008-05-08
traceroute can be installed from the repositories. (sudo apt-get install traceroute)

---

### Post by philipsone on 2008-05-08
> **brigux said:**
> fun...

can you 
```
wget 72.14.207.99
```
```
traceroute 72.14.207.99
```

> **rickh57 said:**
> traceroute can be installed from the repositories. (sudo apt-get install traceroute)

ian@MonOldTosh:~$ sudo apt-get install traceroute
Reading package lists... Done
Building dependency tree... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package traceroute has no installation candidate
ian@MonOldTosh:~$

---

### Post by unutbu on 2008-05-08
philipsone, you say you have another computer that can connect to the internet via the same router. What domain name server does it use? If it is a linux box, check /etc/resolv.conf. If it is a Windows box, I think you run the command ifconfig, but I'm pretty shady here.

Obviously, from your successful `wget 72.14.207.99` you can connect to the internet using numeric ip addresses, the problem is in resolving names -- probably something to do with /etc/resolv.conf.

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> philipsone, you say you have another computer that can connect to the internet via the same router. What domain name server does it use? If it is a linux box, check /etc/resolv.conf. If it is a Windows box, I think you run the command ifconfig, but I'm pretty shady here.

Obviously, from your successful `wget 72.14.207.99` you can connect to the internet using numeric ip addresses, the problem is in resolving names -- probably something to do with /etc/resolv.conf.

Thanks. Yes I think you are onto it. I can connect using numeric ip addresses. 
The other computer is a Windows box and as for which domain name server it uses I am not too sure ifconfig does not run. However is it here:
Name	[00000001] Intel(R) PRO/100 VE Network Connection
Adapter Type	Ethernet 802.3
Product Type	Intel(R) PRO/100 VE Network Connection
Installed	Yes
PNP Device ID	PCI\VEN_8086&DEV_103D&SUBSYS_00011179&REV_83\4&16793A72&0&40F0
Last Reset	08/05/2008 08:44
Index	1
Service Name	E100B
IP Address	192.168.1.6
IP Subnet	255.255.255.0
Default IP Gateway	192.168.1.1
DHCP Enabled	Yes
DHCP Server	192.168.1.1
DHCP Lease Expires	08/05/2008 20:45
DHCP Lease Obtained	08/05/2008 19:45
MAC Address	00:08:0D:93:0D:C4
Memory Address	0xC2004000-0xC2004FFF
I/O Port	0x00003000-0x0000303F
IRQ Channel	IRQ 11
Driver	c:\windows\system32\drivers\e100b325.sys (6.04.14.0000 built by: WinDDK, 137.50 KB (140,800 bytes), 10/11/2003 11:35)


Regarding /etc/resolv.conf. 
If on run it I get 
bash: /etc/resolv.conf: Permission denied

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> philipsone, you say you have another computer that can connect to the internet via the same router. What domain name server does it use? If it is a linux box, check /etc/resolv.conf. If it is a Windows box, I think you run the command ifconfig, but I'm pretty shady here.

Obviously, from your successful `wget 72.14.207.99` you can connect to the internet using numeric ip addresses, the problem is in resolving names -- probably something to do with /etc/resolv.conf.

ps. love the name...

---

### Post by unutbu on 2008-05-08
On the windows box, try 

```
ipconfig /all
```

Look for any line related to "DNS" or "nameserver".

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> On the windows box, try 

```
ipconfig /all
```

Look for any line related to "DNS" or "nameserver".

DNS Servers............:192.168.1.1

---

### Post by unutbu on 2008-05-08
What do you get when you run

```
dig @192.168.1.1 yahoo.com
```

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> What do you get when you run

```
dig @192.168.1.1 yahoo.com
```

ian@MonOldTosh:~$ dig @192.168.1.1 yahoo.com

; <<>> DiG 9.3.2 <<>> @192.168.1.1 yahoo.com
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2896
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 7, ADDITIONAL: 2

;; QUESTION SECTION:
;yahoo.com.                     IN      A

;; ANSWER SECTION:
yahoo.com.              300     IN      A       66.94.234.13
yahoo.com.              300     IN      A       216.109.112.135

;; AUTHORITY SECTION:
yahoo.com.              168293  IN      NS      ns2.yahoo.com.
yahoo.com.              168293  IN      NS      ns3.yahoo.com.
yahoo.com.              168293  IN      NS      ns4.yahoo.com.
yahoo.com.              168293  IN      NS      ns5.yahoo.com.
yahoo.com.              168293  IN      NS      ns6.yahoo.com.
yahoo.com.              168293  IN      NS      ns8.yahoo.com.
yahoo.com.              168293  IN      NS      ns1.yahoo.com.

;; ADDITIONAL SECTION:
ns6.yahoo.com.          168293  IN      A       202.43.223.170
ns8.yahoo.com.          168293  IN      A       202.165.104.22

;; Query time: 2112 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri May  9 09:15:10 2008
;; MSG SIZE  rcvd: 217

ian@MonOldTosh:~$

---

### Post by unutbu on 2008-05-08
Hm. That's interesting. The `dig` command asks your router what the ip address of yahoo.com is. It succeeded!

Okay, now what do you get when you type

```
dig yahoo.com
```

This is the same thing, but dig should now consult /etc/resolv.conf and querie the nameserver listed there. You should get the same thing...

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> Hm. That's interesting. The `dig` command asks your router what the ip address of yahoo.com is. It succeeded!

Okay, now what do you get when you type

```
dig yahoo.com
```

This is the same thing, but dig should now consult /etc/resolv.conf and querie the nameserver listed there. You should get the same thing...

ian@MonOldTosh:~$ dig yahoo.com

; <<>> DiG 9.3.2 <<>> yahoo.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31216
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 7, ADDITIONAL: 2

;; QUESTION SECTION:
;yahoo.com.                     IN      A

;; ANSWER SECTION:
yahoo.com.              300     IN      A       66.94.234.13
yahoo.com.              300     IN      A       216.109.112.135

;; AUTHORITY SECTION:
yahoo.com.              166453  IN      NS      ns8.yahoo.com.
yahoo.com.              166453  IN      NS      ns1.yahoo.com.
yahoo.com.              166453  IN      NS      ns2.yahoo.com.
yahoo.com.              166453  IN      NS      ns3.yahoo.com.
yahoo.com.              166453  IN      NS      ns4.yahoo.com.
yahoo.com.              166453  IN      NS      ns5.yahoo.com.
yahoo.com.              166453  IN      NS      ns6.yahoo.com.

;; ADDITIONAL SECTION:
ns6.yahoo.com.          166453  IN      A       202.43.223.170
ns8.yahoo.com.          166453  IN      A       202.165.104.22

;; Query time: 2098 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Fri May  9 09:45:57 2008
;; MSG SIZE  rcvd: 217

ian@MonOldTosh:~$

---

### Post by unutbu on 2008-05-08
Hm, everything seems to be in order.

What do you get if you 

```
ping -c1 yahoo.com
```

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> Hm, everything seems to be in order.

What do you get if you 

```
ping -c1 yahoo.com
```

PING yahoo.com (216.109.112.135) 56(84) bytes of data.

- - - yahoo.com ping statistics - - -
1 packets transmitted, 0 received, 100% packet loss, time 0ms

---

### Post by unutbu on 2008-05-08
Hm. I think I was wrong when I said this was a DNS problem. The output of the two ping commands you've posted both show the numeric ip address of the ping targets: google.com and yahoo.com. I should have caught that. The problem lies elsewhere.

I'm grasping at straws here, as this problem seems to be beyond my level of knowledge. But, if you are willing to try one more thing, do this:

```
sudo iptables -L

```

This will give you the current list of firewall rules on your machine. The default setting looks like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

If your output looks the same, it means your firewall is letting everything pass through, and you can rule out the machine's firewall as the problem.

The only other thing I can think of is that your router has firewall rules which are blocking internet access to your linux box. If you've checked those settings and they look fine, then I'm at a total loss. Sorry.

---

### Post by philipsone on 2008-05-08
> **unutbu said:**
> Hm. I think I was wrong when I said this was a DNS problem. The output of the two ping commands you've posted both show the numeric ip address of the ping targets: google.com and yahoo.com. I should have caught that. The problem lies elsewhere.

I'm grasping at straws here, as this problem seems to be beyond my level of knowledge. But, if you are willing to try one more thing, do this:

```
sudo iptables -L

```

This will give you the current list of firewall rules on your machine. The default setting looks like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

If your output looks the same, it means your firewall is letting everything pass through, and you can rule out the machine's firewall as the problem.

The only other thing I can think of is that your router has firewall rules which are blocking internet access to your linux box. If you've checked those settings and they look fine, then I'm at a total loss. Sorry.

My output does look the same.
I'm continually rechecking the router settings as best I can and will persevere.
Thanks unutbu so much....

---

### Post by philipsone on 2008-05-12
Hi Again

There is a happy ending (restart).

Summary:
I installed ubuntu 6.06 (from a downloaded Live CD) onto a 7 years old Toshiba Satellite (S2800-500) laptop with 256kb ram.
(Sorry I hastily said before it was 13 years old).
The reason I chose 6.06 was because of my limited RAM. The more recent Live CD versions appeared to require more than 256kb RAM.

6.06 installed OK except I could not get the internet up in spite of all your help. We tried.

I tried openSUSE in various forms and got the internet up with a few tweaks (disable IPv6) but got other problems (including sound).

I downloaded Ubuntu 8.04, yes Hardy Heron. I chose the alternate CD option which said it needed a minimum 256kb ram.
The Live CD needed 384kb RAM.

Result:
IT ALL WORKED straight out of the box.  :lolflag:
It's a bit slow (Pentium III) but it all works.

It runs like a dream.
[www.3wiw.com](www.3wiw.com)

Thanks again for your help.

---

### Post by unutbu on 2008-05-12
I'm really glad you found a solution! Congratulations! =D>

---

