---
title: "enabling my wifi card"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by blkman on 2006-07-20
Hello all,
absolute beginner here, noob?.  Anyhoot, have spent last five days or so trying to get my compaq presario and wifi to work, have tried all of the ndiswrapper, driver patches, everything seems ok except that my interface aren't being read, and that my card has been disabled and needs to be enabled.  I do not have the fn+f2 capability(it just changes the brightness of my screen), so.....Someone help, please!!! Is there a command propmt that i can put in from the terminal as root that will allow me to enable card and get rid of network interface problems?....The cpu does recognize card, but says i am using an invalid driver?, and that i have a fatal error when i input ndiswrapper -l, it does accept ndiswrapper -m, but not ndisrapper modprobe?, i do have eth1 as my wireless option(Took 3 days), but it will not configure, even with static address...I do believe i am an expert at this now!!](*,) :twisted:

---

### Post by bensexson on 2006-07-20
What chipset are you using?  Paste the output from ifconfig -a and iwconfig.

---

### Post by blkman on 2006-07-20
lo        no wireless extensions.

eth3      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by blkman on 2006-07-20
root@joshua:/home/joshua# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:A8:6A:C0
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fea8:6ac0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6086 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4991819 (4.7 MiB)  TX bytes:1110583 (1.0 MiB)
          Interrupt:10 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:0B:CD:75:EE:52
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:255 Base address:0x4000

eth3      Link encap:UNSPEC  HWaddr 00-0B-CD-71-A0-85-E9-F5-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by blkman on 2006-07-20
Thanks, there you go.....](*,) ](*,)

---

### Post by bensexson on 2006-07-21
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

---

