---
title: "libx11 help"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by nanxy85 on 2008-03-05
when i type the following code to install libx11:
apt-get install libx11-6 libx11-dev libxt6 libxt6-dbg libxext6 libxtst-dev libxtst6 xlibs-dbg xlibs-dev

i got the following error:

The following packages are BROKEN:
  libx11-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1240kB of archives. After unpacking 4432kB will be used.
The following packages have unmet dependencies:
  libx11-dev: Depends: libx11-6 (= 2:1.0.0-0ubuntu9.1) but 2:1.1.1-1ubuntu4 is installed.
              Depends: x11proto-core-dev (>= 6.8.99.8-1) which is a virtual package.
              Depends: x11proto-kb-dev which is a virtual package.
              Depends: x11proto-input-dev which is a virtual package.
              Depends: libxau-dev which is a virtual package.
              Depends: libxdmcp-dev which is a virtual package.
              Depends: x11proto-kb-dev which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.


this repositories wont not download:
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2:) Could not resolve 'archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) Could not resolve 'archive.ubuntu.com'

how to get it right?

---

### Post by jeffus_il on 2008-03-05
Run Synaptic Package Manager and run Edit->Fix broken packages.
Then ```
 ping archive.ubuntu.com
```
and let us know what happens.

---

### Post by nanxy85 on 2008-03-05
ping: unknown host archive.ubuntu.com

---

### Post by jeffus_il on 2008-03-05
I think you networking is not working. can you post the output of```
 ifconfig
``` and ```
iwconfig
``` in a terminal?

---

### Post by zvacet on 2008-03-05
In** system>admin<software sources **change server.

---

### Post by nanxy85 on 2008-03-06
for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:13:72:78:63:47  
          inet addr:10.64.103.187  Bcast:10.64.103.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe78:6347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1276398 (1.2 MB)  TX bytes:214588 (209.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:BF:C9:AD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xe000 


for iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:""  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Encryption key:off
          Power Management:off
          Link Quality=37/100  Signal level=12/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by jeffus_il on 2008-03-06
My guess is that you are using NetworkManager, the acx driver you are using with your card does not supply the functionality that  NetworkManager  needs. Try click manual config on the NetworkManager icon and set up your connection manually. If this still doesn't work uninstall NetworkManager and use the manual network setup from the system menu, this will definitely work because your driver is installed OK from the iwconfig output.

---

