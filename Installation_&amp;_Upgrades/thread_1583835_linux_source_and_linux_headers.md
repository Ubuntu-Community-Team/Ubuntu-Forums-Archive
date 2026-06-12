---
title: "linux source and linux headers"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by nothreat33 on 2010-09-28
I'm installing rt61 wireless drivers. I'm getting an error during make. I've looked around the internet so let me first say that I have installed build-essential, linux-source, and linux-headers.

The error:
> michael@michael-desktop:~/Downloads/rt61-cvs-2007051818/Module$ sudo make
[sudo] password for michael: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-19-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-19-generic'
rt61.ko failed to build!
make: *** [module] Error 1
michael@michael-desktop:~

I've gotten the impression that this error is because kernel/bounds.c is part of linux-source not linux-headers. So it can't find it because it's entering the linux-headers directory. 

for clarity this is how my /usr/src is organized:

> root@michael-desktop:/lib/modules# cd /usr/src
root@michael-desktop:/usr/src# ls

                  linux-headers-2.6.35-19          linux-source-2.6.35.tar.bz2
glibc             linux-headers-2.6.35-19-generic  nvidia-current-256.53
linux             linux-source-2.6.35              uClibc-0.9.30.2.tar.bz2

root@michael-desktop:/usr/src# cd linux-source-2.6.35

root@michael-desktop:/usr/src/linux-source-2.6.35# ls

debian  debian.master  linux-source-2.6.35  linux-source-2.6.35.tar.bz2

root@michael-desktop:/usr/src/linux-source-2.6.35# cd linux-source-2.6.35

root@michael-desktop:/usr/src/linux-source-2.6.35/linux-source-2.6.35# ls

arch     Documentation  init    MAINTAINERS  REPORTING-BUGS  tools
block    drivers        ipc     Makefile     samples         ubuntu
COPYING  firmware       Kbuild  mm           scripts         usr
CREDITS  fs             kernel  net          security        virt
crypto   include        lib     README       sound

root@michael-desktop:/usr/src/linux-source-2.6.35/linux-source-2.6.35# 


I've thought of a few things to do. Edit the Makefile (don't really know how to do that). Link linux-source to linux-headers. or move around the linux-source data up one so it's usr/src/linux-source2.6.35/ and not /usr/src/linux-source2.6.35/linux-source2.6.35.

But I'm not sure exactly what to do. But I feel like I'm close.

---

### Post by sgosnell on 2010-09-28
You extracted the source tarfile one level too low.  Move it a level higher, to /etc/src, and then extract it, and you should be ok.

---

### Post by nothreat33 on 2010-09-28
I moved the source folder up one.

> michael@michael-desktop:/usr/src/linux-source-2.6.35$ ls
arch     Documentation  init    MAINTAINERS  REPORTING-BUGS  tools
block    drivers        ipc     Makefile     samples         ubuntu
COPYING  firmware       Kbuild  mm           scripts         usr
CREDITS  fs             kernel  net          security        virt
crypto   include        lib     README       sound
michael@michael-desktop:/usr/src/linux-source-2.6.35$

Didn't work same error. :/
> root@michael-desktop:/home/michael/Downloads/rt61-cvs-2007051818/Module# sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-19-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-19-generic'
rt61.ko failed to build!
make: *** [module] Error 1
root@michael-desktop:/home/michael/Downloads/rt61-cvs-2007051818/Module# 

---

### Post by nothreat33 on 2010-10-05
Downloaded the latest compat-wireless: [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)

Extracted to home directory

saved patch ([http://patches.aircrack-ng.org/channel-negative-one-maxim.patch](http://patches.aircrack-ng.org/channel-negative-one-maxim.patch)) to ~/compat-wireless-2010-10-04/net/wireless

patched:
```
root@michael-desktop:/home/michael/compat-wireless-2010-10-04/net/wireless# patch -Np3 -i patch1.txt 
patching file chan.c
Hunk #1 succeeded at 50 (offset 1 line).
Hunk #2 succeeded at 80 (offset 1 line).
root@michael-desktop:/home/michael/compat-wireless-2010-10-04/net/wireless#
```

I have chipset: RaLink RT2561/RT61

selecting driver:
```
root@michael-desktop:/home/michael/compat-wireless-2010-10-04# ./scripts/driver-select rt2x00
Processing new driver-select request...
Backing up makefile: Makefile.bk
Backing up makefile: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backing up makefile: net/wireless/Makefile.bk
Backing up makefile: drivers/net/Makefile.bk
Backing up makefile: drivers/ssb/Makefile.bk
root@michael-desktop:/home/michael/compat-wireless-2010-10-04#
```

ran make, no problems.
output:
[http://pastebin.ubuntu.com/506667/](http://pastebin.ubuntu.com/506667/)

ran make install, some errors but it completed.
output:
[http://pastebin.ubuntu.com/506669/](http://pastebin.ubuntu.com/506669/)

ran make unload:
```
root@michael-desktop:/home/michael/compat-wireless-2010-10-04# make unload
Stoping bluetooth service..
 * bluetooth is not running
Unloading rt61pci...
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
root@michael-desktop:/home/michael/compat-wireless-2010-10-04#
```

loaded wireless module:
```
root@michael-desktop:/home/michael/compat-wireless-2010-10-04# modprobe rt61pci
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
root@michael-desktop:/home/michael/compat-wireless-2010-10-04#
```

setting card on channel:
```
root@michael-desktop:~# ifconfig wlan0 down
root@michael-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6664-6664-6A
          Power Management:off
          
root@michael-desktop:~# airmon-ng start wlan0 6


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
3214	NetworkManager
3217	avahi-daemon
3218	avahi-daemon
3221	dhclient
3222	wpa_supplicant


Interface	Chipset		Driver

wlan0		Ralink 2561 PCI	rt61pci - [phy0]
				(monitor mode enabled on mon0)

root@michael-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:6664-6664-6A
          Power Management:off
          
mon0      IEEE 802.11bg  Mode:Monitor  Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

testing injection with aireplay:
```

root@michael-desktop:~#  aireplay-ng --test -e R9FV0 -a 00:1F:90:E5:A9:D1 mon0
14:07:29  Waiting for beacon frame (BSSID: 00:1F:90:E5:A9:D1) on channel -1
14:07:30  mon0 is on channel -1, but the AP uses channel 6
root@michael-desktop:~#

```

running airodump with command: 
 airodump-ng -c 6 -w capture.out --bssid 00:1F:90:E5:A9:D1 mon0

```
CH  6 ][ Elapsed: 28 s ][ 2010-10-05 14:09 ][ fixed channel mon0: -1                                         
                                                                                                                       
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER AUTH ESSID                                    
                                                                                                                       
 00:1F:90:E5:A9:D1  -49  80      212       25    0   6  54e. WEP  WEP         R9FV0                                    
                                                                                                                       
 BSSID              STATION            PWR   Rate    Lost  Packets  Probes 
```

---

