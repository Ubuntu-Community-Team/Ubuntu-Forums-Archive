---
title: "CISCO VPN Client on Lucid-Lynx Beta 2"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eugen_nicoara on 2010-04-09
Hello,
I'm trying to install CISCO VPN Client on Lucid-Lynx Beta 2 release.

Here is what I get:

[FONT="Courier New"]....
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.32-19-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.32-19-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.32-19-generic/build SUBDIRS=/tmp/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-19-generic'
  CC [M]  /tmp/vpnclient/interceptor.o
/tmp/vpnclient/interceptor.c: In function ‘interceptor_init’:
/tmp/vpnclient/interceptor.c:132: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/vpnclient/interceptor.c:133: error: ‘struct net_device’ has no member named ‘get_stats’
/tmp/vpnclient/interceptor.c:134: error: ‘struct net_device’ has no member named ‘do_ioctl’
/tmp/vpnclient/interceptor.c: In function ‘add_netdev’:
/tmp/vpnclient/interceptor.c:271: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/vpnclient/interceptor.c:272: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/tmp/vpnclient/interceptor.c: In function ‘remove_netdev’:
/tmp/vpnclient/interceptor.c:294: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/tmp/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/tmp/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-19-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".[/FONT]

I've searched the net and I've found out almost the same error was linked with some specific kernel version ([https://answers.launchpad.net/ubuntu/+question/16053]("https://answers.launchpad.net/ubuntu/+question/16053")).

Any idea what to do? More info on system config below:

[FONT="Courier New"]sudo dpkg -l linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
un  linux-headers                          <none>                                 (no description available)
un  linux-headers-2.6                      <none>                                 (no description available)
un  linux-headers-2.6-686                  <none>                                 (no description available)
un  linux-headers-2.6-amd64                <none>                                 (no description available)
ii  linux-headers-2.6.32-19                2.6.32-19.28                           Header files related to Linux kernel version 2.6.32
ii  linux-headers-2.6.32-19-generic        2.6.32-19.28                           Linux kernel headers for version 2.6.32 on x86/x86_64
ii  linux-headers-generic                  2.6.32.19.20                           Generic Linux kernel headers

uname -a
Linux test 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686 GNU/Linux[/FONT]


Thanks!

---

### Post by eugen_nicoara on 2010-04-22
I'm sorry guys but I don't have good news. I've just updated the system to Realease Candidate and the problem it's still not solved.

[FONT="Courier New"]
....
Directory containing linux kernel source code [/lib/modules/2.6.32-21-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.32-21-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.32-21-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/eugen/kits/ciscovpnclient/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/eugen/kits/ciscovpnclient/vpnclient/linuxcniapi.o
  CC [M]  /home/eugen/kits/ciscovpnclient/vpnclient/frag.o
  CC [M]  /home/eugen/kits/ciscovpnclient/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/eugen/kits/ciscovpnclient/vpnclient/interceptor.o
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c: In function ‘interceptor_init’:
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c:132: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c:133: error: ‘struct net_device’ has no member named ‘get_stats’
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c:134: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c: In function ‘add_netdev’:
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c:271: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c:272: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c: In function ‘remove_netdev’:
/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.c:294: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/eugen/kits/ciscovpnclient/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/eugen/kits/ciscovpnclient/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".[/FONT]

---

### Post by glasen on 2010-04-22
Here is an URL with instructions to compile the Cisco VPN client with kernel version 2.6.30+ :

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

BTW, in most cases the open source client "vpnc" is a drop-in replacement for the Cisco client. It even integrates nicely into the network-manager.

---

### Post by xir_ on 2010-04-22
> **glasen said:**
> Here is an URL with instructions to compile the Cisco VPN client with kernel version 2.6.30+ :

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

BTW, in most cases the open source client "vpnc" is a drop-in replacement for the Cisco client. It even integrates nicely into the network-manager.


ill confirm this, by instaling that package i can connect to my uni vnc without and issue and it has very easy  (and sexy) networkmanager integration.

---

### Post by forumache on 2010-04-23
sudo aptitude install network-manager-vpnc-gnome

it will also pull network-manager-vpnc and vpnc

then:

left click on the network icon in the upper right panel,
VPN Conections | Configure VPN
Add, select Cisco Compatible Protocol (vpnc)
Create and fill in the details.

then, in order to connect:
left click on the network icon in the upper right panel,
VPN Conections | Connect to OUCS (or whatever you named the connection).

Done!

to disconnect:
left click on the network icon in the upper right panel,
VPN Conections | Disconnect from OUCS (or whatever you named the connection).


Simple. As Linux is ;)

---

### Post by SeanBlader on 2010-04-26
I wish it went as easy for me as it did for forumache, but it looks like the VPN connects but then I can't transfer any data. I don't even get pings, any diagnosis tips?

Figured it out, needed to setup a route in network manager. Now if I can just figure out why the terminal server session crashed, later...

---

### Post by eugen_nicoara on 2010-04-27
Thank you glasen! Problem solved.

---

