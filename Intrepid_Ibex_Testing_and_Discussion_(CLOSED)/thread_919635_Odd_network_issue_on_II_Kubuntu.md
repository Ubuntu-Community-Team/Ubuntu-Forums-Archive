---
title: "Odd network issue on II Kubuntu"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Crinos512 on 2008-09-14
I cannot seem to get my network interface working correctly. I want it to have an ip address of [COLOR="#800080"]10.125.125.125[/COLOR], and netmask of [COLOR="#800080"]255.255.255.0[/COLOR] so that it will be on the same subnet as the rest of the PCs on my network, however try as I may I cannot seem to get the network functional.

I seem to have an ip address of [COLOR="Purple"]0.0.0.0[/COLOR], and netmask of [COLOR="#800080"]0.0.0.0[/COLOR]. 

```

crinos@Fortress:~$ [COLOR="Blue"]cat /etc/network/interfaces[/COLOR]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
[COLOR="#0000ff"]        address 10.125.125.125
        netmask 255.255.255.0[/COLOR]
        network 10.125.125.0
        broadcast 10.125.125.255

crinos@Fortress:~$ [COLOR="#0000ff"]ifconfig eth0[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:28:1a:a1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28296 (28.2 KB)  TX bytes:5207 (5.2 KB)
          Interrupt:248 Base address:0x2000

```

any ideas? any help in this matter would be appreciated. :(

---

### Post by Crinos512 on 2008-09-14
I tried the following command:
```
crinos@Fortress:~$ [COLOR="Blue"]sudo /etc/init.d/NetworkManager restart[/COLOR]
Restarting Network connection manager daemon: NetworkManager.

```

and the KNetworkManager started animating ... but then went grey again.

when I hover over it there is a tooltop that says:
```
Device: eth0
State: Disconnected
```

:confused:

---

### Post by Crinos512 on 2008-09-14
More trouble shooting info... 
```
crinos@Fortress:~$ [COLOR="#000080"]sudo ifup eth0 [/COLOR]         
ifup: interface eth0 already configured
crinos@Fortress:~$ [COLOR="#000080"]sudo ifconfig eth0 up[/COLOR]
crinos@Fortress:~$ [COLOR="#000080"]sudo ifconfig eth0[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:28:1a:a1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:149584 (149.5 KB)  TX bytes:8627 (8.6 KB)
          Interrupt:248 Base address:0x2000

crinos@Fortress:~$ [COLOR="Navy"]dmesg | grep eth[/COLOR]
[    4.152792] eth0: RTL8168b/8111b at 0xffffc20000332000, 00:e0:4d:28:1a:a1, XID 38000000 IRQ 2296
[    5.788184] Driver 'sr' needs updating - please use bus_type methods
[    5.792171] Driver 'sd' needs updating - please use bus_type methods
[   41.062856] r8169: eth0: link up
[   41.062862] r8169: eth0: link up
[ 8140.663133] r8169: eth0: link down
[ 8142.797607] r8169: eth0: link up
[ 8151.027982] r8169: eth0: link down
[ 8160.122896] r8169: eth0: link up
[ 8991.274316] r8169: eth0: link up
[ 9062.604789] r8169: eth0: link up

```
anything standing out to anyone yet?

---

### Post by Crinos512 on 2008-09-14
more TS... code

```
crinos@Fortress:~$ [COLOR="Blue"]lshw -C network[/COLOR]
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:4d:28:1a:a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
crinos@Fortress:~$ [COLOR="#000080"]lsmod | grep r81*[/COLOR]
r8169                  40196  0


```

---

### Post by Crinos512 on 2008-09-15
```
crinos@Fortress:~$ [COLOR="Blue"]sudo ethtool eth0[/COLOR]
[sudo] password for crinos:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

```

...similar problems were reported in Gutsy's RC. [ [link]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=538448") ] I'll try some of those fixes and let it be known here.

---

### Post by Crinos512 on 2008-09-15
OK the fixed from the link in the above post did not work for me.

Hmmm... looks to be related to an existing Bug [[ 208012 ]]("https://bugs.launchpad.net/ubuntu/+bug/208012")

...will try the "replace the driver" fix and report back.

---

### Post by Crinos512 on 2008-09-20
Grr... I was not able to successfully build the driver on my system.

I get as far as [COLOR="Blue"]sudo make clean modules[/COLOR] and I get:

```
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.008.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/usr/src/r8168-8.008.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.008.00/src'
make -C /lib/modules/2.6.27-2-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-2-generic'
scripts/Makefile.build:41: /src/Makefile: [COLOR="Red"]No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.[/COLOR]
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-2-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.008.00/src'
make: *** [modules] Error 2
```

---

### Post by Crinos512 on 2008-09-20
Also there appears to be a kernel update in the repos... version 2.6.27.3.3. I'm still on 2.6.27.2.

Maybe an upgrade will fix this.

---

