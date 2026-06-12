---
title: "[SOLVED] intrepid rt73 broken"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chronographer on 2008-09-30
issues: rt73 just broke in the 2.6.27-4 kernel.

I get this error in dmesg:
```
[ 2051.352019] usb 8-6: new high speed USB device using ehci_hcd and address 4
[ 2051.656135] usb 8-6: configuration #1 chosen from 1 choice
[ 2051.921165] phy2: Selected rate control algorithm 'pid'
[ 2051.922084] Registered led device: rt73usb-phy2:radio
[ 2051.922219] Registered led device: rt73usb-phy2:assoc
[ 2051.922347] Registered led device: rt73usb-phy2:quality
[ 2051.927324] firmware: requesting rt73.bin
[ 2051.932318] phy2 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
```

So it seems the firmware doesn't load. I get this for modprobe rt73:FATAL: Module rt73 not found.

and there is an issue with compiling drivers myself (see [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4993&p=30716#p30716](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4993&p=30716#p30716) ) 

So... Could someone in the know let me know how to fix this, I could try compiling the rt73-source package which is available, but m-a gave errors like 'couldn't find package' or whatever...

Thanks. Alex

---

### Post by norgur on 2008-10-05
First, you will need to copy the firmware file rt73.bin from **/lib/firmware** to **/lib/firmware/`uname -r`**, which is through the kernel update to 2.6.27 another directory than it was before, what explains the firmware issue:
```
sudo cp /lib/firmware/rt73.bin /lib/firmware/`uname -r`
```

On every Distribution upgrade, 3rd party modules get disabled. So re-add the **rt73**-entrie to your **/etc/modules**.
After doing that, verify that the modules **rt73usb**, **rt2500usb** and **rt2x00** are still blacklistet in **/etc/modprobe.d/blacklist**. If not, just add those lines to the blacklist file (you will need superuser-rights to open it):
```
blacklist rt2500usb
blacklist rt2x00usb
blacklist rt73usb
```
Now, you should unload the modules, you blacklisted the line before and load the correct rt73-module:
```
sudo rmmod rt2500usb
sudo rmmod rt2x00usb
sudo rmmod rt73usb
```
and to load the module: ```
sudo modprobe rt73
sudo ifup wlan0
``` if he complains, that "wlan0" (or whatever you called your wlan-device) can't be brought up, just reboot or in case you own an usb-wlan adaptor, replug it. That should bring your device up again.
If it still won't work, boot your old kernel, go online and download the packages **&#314;inux-headers-2.6.27-5-generic** and **linux-headers-2.6.27-5**: ```
sudo apt-get install linux-headers-2.6.27-5 linux-headers-2.6.27-5-generic
```
And the sources for the rt73-kernel module: 
```
sudo wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz -O /usr/src/rt73-cvs-daily.tar.gz
``` then boot to your new kernel and follow this guide: [HOWTO: RT73 (RT71) serialmonkey drivers]("http://ubuntuforums.org/showthread.php?t=400236") (you can skip the part with the download of the module sources, of course)

---

### Post by chronographer on 2008-10-07
firstly, thank for your response. I have had some frustrating times the last few days with this card.

now to the details..

I have no file called /lib/firmware/rt73.bin . i am aware that modules I install myself need to be installed again by myself, and have done this the past two years.

But, now I get this error when compiling the serialmonkey module (the daily version, in this case september 30 2008:

```
alex@quadruped:/usr/src/rt73-cvs-2008093011/Module$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-4-generic'
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/rtmp_init.o
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c: In function &#8216;KillThreads&#8217;:
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c:187: error: implicit declaration of function &#8216;kill_proc&#8217;
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c: In function &#8216;LoadFirmware&#8217;:
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c:1627: warning: assignment discards qualifiers from pointer target type
make[2]: *** [/usr/src/rt73-cvs-2008093011/Module/rtmp_init.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2008093011/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-4-generic'
rt73.ko failed to build!
make: *** [module] Error 1
```

so it is a problem with the drivers, they won't compile... I don't know enough about the code to go digging around in there.

I am about to try one last reboot, as I blacklisted a few new drivers which werent blacklisted before, and rt73usb was trying to be used! so lets hope for the best, and I will edit this in a couple minutes and let you know what happens.

Thanks for your help

No good, wireless cards don't work I have tried both a belkin fsd7050 (rt73) and a dlink dwl g122 (ralink too)

---

### Post by norgur on 2008-10-07
I got this error today, too and read about several people having it. I reactivated the built-in module from ubuntu and purged network manager... now i got a connection... not an amazing one, but better than nothing ;)

---

### Post by chronographer on 2008-10-07
How do you mean 'reactivated the module' ? modprobe rt73 ? that doesn't work for me... Oh took it off blacklist? I tried that too!

The funny thing is I bought a second wireless card to use instead and *it uses the same bloody chipset!*  :(

I removed all listings in blacklist and get a network interface, but it wont connect.

```
alex@quadruped:~$ rutilt
Internet Systems Consortium DHCP Client V3.1.1Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:17:9a:c3:7f:10
Sending on   LPF/wlan1/00:17:9a:c3:7f:10
Sending on   Socket/fallback
receive_packet failed on wlan1: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
Helper : Can't bring interface up.
Code : 2
^CCan't read in socket.
Code : 4
alex@quadruped:~$ rutilt
Internet Systems Consortium DHCP Client V3.1.111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111111
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
11111111wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:17:9a:c3:7f:10
Sending on   LPF/wlan1/00:17:9a:c3:7f:10
Sending on   Socket/fallback
receive_packet failed on wlan1: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Can't get access point Mac address.
Code : 19

```

and if I use ifup & down with this is the /etc/network/interfaces file:
```
auto wlan0
iface wlan0 inet static
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid TheEther
	pre-up iwconfig wlan0 key C5E90204986D09C602DE18859E
	address 192.168.1.9
	netmask 255.255.255.0
	gateway 192.168.1.1
	wireless-key C5E90204986D09C602DE18859E
	wireless-essid TheEther
	dns-nameservers 192.168.1.1
```

I get this: 

```
alex@quadruped:~$ sudo ifup wlan0
SIOCSIFFLAGS: No such file or directory
Failed to bring up wlan0.
alex@quadruped:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TheEther"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Please help!

---

### Post by norgur on 2008-10-07
that is the broken network manager 0.7, the intrepid beta uses. purge the network-manager with ```
sudo apt-get purge network-manager
``` and then set up your wlan manually. If you never did that before: the [Debian Reference]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html") gives the necessary instructions.

---

### Post by chronographer on 2008-10-08
Unfortunately its not that either... I have always uninstalled network-manager, I reinstalled it hoping something different would happen. Also tried wicd, rutilt and all in vain.

Thanks for trying, but no good. I have used this USB stick for a couple of years, starting on debian, I know how to get it working. My big issues are that the kernel driver is now broken, and I can't compile my own drivers due to serial monkeys code not compiling.

I have invested in 10 m of blue cable now, so problem solved for the time being!

---

### Post by chronographer on 2008-10-09
New kernel today, to troubles apart from the rt73 issue.

```
:/usr/src/rt73-cvs-2008093011/Module$ sudo make
[sudo] password for alex: 
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-6-generic'
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/rtmp_main.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/mlme.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/connect.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/rtusb_bulk.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/rtusb_io.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/sync.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/assoc.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/auth.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/auth_rsp.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/rtusb_data.o
  CC [M]  /usr/src/rt73-cvs-2008093011/Module/rtmp_init.o
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c: In function ‘KillThreads’:
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c:187: error: implicit declaration of function ‘kill_proc’
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c: In function ‘LoadFirmware’:
/usr/src/rt73-cvs-2008093011/Module/rtmp_init.c:1627: warning: assignment discards qualifiers from pointer target type
make[2]: *** [/usr/src/rt73-cvs-2008093011/Module/rtmp_init.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2008093011/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-6-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```

using kernel:  2.6.27-6-generic

I would like to get this fixed.

---

### Post by _oOMOo_ on 2008-10-12
chronographer, the legacy RT73 driver now compiles on 2.6.27 - you need to apply the patch on the thread:

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4993&p=30926#p30926]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4993&p=30926#p30926")

I think you may need to edit Module/rtmp_init.c as well on line 1627 and change:

```
data = fw_entry->data;
```

to 

```
data = (u8 *)fw_entry->data;
```

then copy the patch tarball to the Module directory and

```
zcat kill_proc5.patch.gz | patch
```

then just make, make install as usual. There's no need to mess around with the firmware from my experience anyway.

The legacy driver is much more stable than the rt73usb driver, it's faster on my system too.

Cheers, Jon (mcmlxxii)

---

### Post by paxmark1 on 2008-10-12
As I posted elsewhere, I was saddened that a company that has given acess to linux developers for years, specifically that the RT73 chipset, does not work out of the box with a the Ununtus.  Very specifically why shouldn't the Hawking 54USB marketed to the linux market with the antenna that really boosts gain that had linux drivers that came with it.  

I tried the beginning of the 101 Ubuntu forum pages of info, it had worked  in the past for how to get and compile the serial monkey drivers and what to blacklist.  No go for compiling.  

And then later, so many updates later and after adding some headers, it is working.  How well, I don't know, but I could find encrypted networks in the nieghborhood. (NOTE - I have a fast enough connection, and am not intending to use wireless at this point.)  So, mine is working now in Kubuntu with the upgrades of Oct. 11.  

Much of the "Serial Monkey" work this has been merged into the kernel into wireless-dev.  I hope it continues to work with the Ubuntus.  

Never tried it, but I understand it has worked flawlessly with RedHat for years.

---

### Post by xjohnthomasx on 2008-10-15
i was having exactly the same issue. had been using the new intrepid rt73usb drivers.. i followed all these instructions. success on the compiling and installing and replacing the new rt73 drivers (legacy drivers). however, my internet STILL won't connect, and now it doesn't properly see all the available wireless networks. they all show with 0 reception, even though it recognizes the ESSID's of the local wireless available nets.. tail gives "wlan0: link timed out" error messages.. says "activation (wlan0) failed for access point ([mynetworkname])"... what else should i try and do? let me know if you need any more info..

---

### Post by hajk on 2008-10-15
> **norgur said:**
> I got this error today, too and read about several people having it. I reactivated the built-in module from ubuntu and purged network manager... now i got a connection... not an amazing one, but better than nothing ;)
That whole issue with the rt73usb driver derives in my experience indeed from the use of network-manager. Haven't had ANY problems with rt73usb on my Linksys WUSB54GC since I decided to get rid of network-manager a few 2.6 kernel versions ago. Pity that Ubuntu seems so focused on using it...

---

### Post by xjohnthomasx on 2008-10-15
Wait a minute, I may have something.. So I blacklisted the recompiled/newly installed legacy rt73 drivers, and i went back to using the rt73usb included initially with intrepid. i was using the Internet as normal, and then it crapped out, and these are the tail logs.. 

> Oct 15 07:53:19 jupiter2 NetworkManager: <debug> [1224071599.522971] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:3D:39:10:96 (LODGER) 
Oct 15 07:55:13 jupiter2 NetworkManager: <debug> [1224071713.601943] periodic_update(): Roamed from BSSID 00:0F:3D:39:10:96 (LODGER) to (none) ((none)) 
Oct 15 07:55:19 jupiter2 NetworkManager: <debug> [1224071719.605557] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:3D:39:10:96 (LODGER) 

****** Connection seemed to crap out around this point!!!********

Oct 15 08:00:01 jupiter2 /USR/SBIN/CRON[9353]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 15 08:03:26 jupiter2 kernel: [ 4474.961767] usb 8-5.2: reset high speed USB device using ehci_hcd and address 4
Oct 15 08:10:01 jupiter2 /USR/SBIN/CRON[9577]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 15 08:17:01 jupiter2 /USR/SBIN/CRON[9828]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 15 08:20:01 jupiter2 /USR/SBIN/CRON[10010]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 15 08:22:12 jupiter2 kernel: [ 5601.528260] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 2.
Oct 15 08:22:12 jupiter2 kernel: [ 5601.528262] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
Oct 15 08:22:12 jupiter2 kernel: [ 5601.528340] phy0 -> rt2x00queue_write_tx_frame: Error - Arrived at non-free entry in the non-full queue 2.
Oct 15 08:22:12 jupiter2 kernel: [ 5601.528341] Please file bug report to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).

****** At this point here, I sudo ifconfig wlan0 down. Then I sudo modprobe -r rt73usb. Then I sudo modprobe rt73usb. Then I sudo ifconfig wlan0 up. Then I reselect the proper network from the NetworkManager drop down, and then it connects and I have internet again! ****************


Oct 15 08:28:48 jupiter2 avahi-daemon[5359]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 15 08:28:48 jupiter2 avahi-daemon[5359]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.100.
Oct 15 08:28:48 jupiter2 dhclient: receive_packet failed on wlan0: Network is down
Oct 15 08:28:48 jupiter2 avahi-daemon[5359]: Withdrawing address record for 192.168.0.100 on wlan0.
Oct 15 08:28:51 jupiter2 NetworkManager: <debug> [1224073731.029387] periodic_update(): Roamed from BSSID 00:0F:3D:39:10:96 (LODGER) to (none) ((none)) 
Oct 15 08:28:55 jupiter2 kernel: [ 6003.929519] usbcore: deregistering interface driver rt73usb
Oct 15 08:28:55 jupiter2 nm-system-settings:    SCPlugin-Ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_00_16_44_7c_a0_e2_0)
Oct 15 08:28:55 jupiter2 NetworkManager: <info>  (wlan0): now unmanaged 
Oct 15 08:28:55 jupiter2 NetworkManager: <info>  (wlan0): device state change: 8 -> 1 
Oct 15 08:28:55 jupiter2 NetworkManager: <info>  (wlan0): deactivating device. 
Oct 15 08:28:55 jupiter2 NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 8501 
Oct 15 08:28:55 jupiter2 modprobe: WARNING: Not loading blacklisted module rt73 
Oct 15 08:28:55 jupiter2 modprobe: WARNING: Not loading blacklisted module rt73 
Oct 15 08:28:55 jupiter2 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Oct 15 08:28:55 jupiter2 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Oct 15 08:28:55 jupiter2 modprobe: WARNING: Not loading blacklisted module rt73 
Oct 15 08:28:55 jupiter2 last message repeated 2 times
Oct 15 08:28:55 jupiter2 NetworkManager: <info>  (wlan0): cleaning up... 
Oct 15 08:28:55 jupiter2 modprobe: WARNING: Not loading blacklisted module rt73 
Oct 15 08:28:55 jupiter2 nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist  
Oct 15 08:28:55 jupiter2 modprobe: WARNING: Not loading blacklisted module rt73 
Oct 15 08:28:55 jupiter2 last message repeated 13 times
Oct 15 08:29:10 jupiter2 kernel: [ 6019.060139] phy0: Selected rate control algorithm 'pid'
Oct 15 08:29:10 jupiter2 kernel: [ 6019.060438] Registered led device: rt73usb-phy0:radio
Oct 15 08:29:10 jupiter2 kernel: [ 6019.060452] Registered led device: rt73usb-phy0:assoc
Oct 15 08:29:10 jupiter2 kernel: [ 6019.060464] Registered led device: rt73usb-phy0:quality
Oct 15 08:29:10 jupiter2 kernel: [ 6019.061014] usbcore: registered new interface driver rt73usb
Oct 15 08:29:10 jupiter2 nm-system-settings:    SCPlugin-Ifupdown: devices added (udi: /org/freedesktop/Hal/devices/net_00_16_44_7c_a0_e2_0, iface: wlan0)
Oct 15 08:29:10 jupiter2 NetworkManager: <info>  wlan0: driver is 'rt73usb'. 
Oct 15 08:29:10 jupiter2 NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Oct 15 08:29:10 jupiter2 NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'. 
Oct 15 08:29:10 jupiter2 NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_16_44_7c_a0_e2_0 
Oct 15 08:29:13 jupiter2 kernel: [ 6022.272165] firmware: requesting rt73.bin
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): preparing device. 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): deactivating device. 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): device state change: 2 -> 3 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2. 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) starting connection 'Auto LODGER' 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto LODGER' has security, but secrets are required. 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Oct 15 08:29:14 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 15 08:29:15 jupiter2 kernel: [ 6023.884609] wlan0: authenticate with AP 00:16:b6:2e:13:f8
Oct 15 08:29:15 jupiter2 kernel: [ 6023.886242] wlan0: authenticated
Oct 15 08:29:15 jupiter2 kernel: [ 6023.886247] wlan0: associate with AP 00:16:b6:2e:13:f8
Oct 15 08:29:15 jupiter2 kernel: [ 6023.888496] wlan0: RX AssocResp from 00:16:b6:2e:13:f8 (capab=0x401 status=0 aid=4)
Oct 15 08:29:15 jupiter2 kernel: [ 6023.888501] wlan0: associated
Oct 15 08:29:15 jupiter2 kernel: [ 6023.889065] wlan0: disassociating by local choice (reason=3)
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  (wlan0): supplicant connection state change: 1 -> 4 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 0 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto LODGER' has security, and secrets exist.  No new secrets needed. 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'ssid' value 'LODGER' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'bssid' value '00:0f:3d:39:10:96' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'auth_alg' value 'SHARED' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0' 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 15 08:29:15 jupiter2 NetworkManager: <info>  Config: set interface ap_scan to 1 
Oct 15 08:29:19 jupiter2 NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Oct 15 08:29:20 jupiter2 NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Oct 15 08:29:21 jupiter2 kernel: [ 6030.477636] wlan0: authenticate with AP 00:0f:3d:39:10:96
Oct 15 08:29:21 jupiter2 kernel: [ 6030.484519] wlan0: authenticated
Oct 15 08:29:21 jupiter2 kernel: [ 6030.484523] wlan0: associate with AP 00:0f:3d:39:10:96
Oct 15 08:29:21 jupiter2 kernel: [ 6030.486778] wlan0: RX AssocResp from 00:0f:3d:39:10:96 (capab=0x431 status=0 aid=1)
Oct 15 08:29:21 jupiter2 kernel: [ 6030.486782] wlan0: associated
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'LODGER'. 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  dhclient started with pid 10598 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 15 08:29:21 jupiter2 dhclient: Internet Systems Consortium DHCP Client V3.1.1
Oct 15 08:29:21 jupiter2 dhclient: Copyright 2004-2008 Internet Systems Consortium.
Oct 15 08:29:21 jupiter2 dhclient: All rights reserved.
Oct 15 08:29:21 jupiter2 dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Oct 15 08:29:21 jupiter2 dhclient: 
Oct 15 08:29:21 jupiter2 dhclient: wmaster0: unknown hardware address type 801
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Oct 15 08:29:21 jupiter2 dhclient: wmaster0: unknown hardware address type 801
Oct 15 08:29:21 jupiter2 dhclient: Listening on LPF/wlan0/00:16:44:7c:a0:e2
Oct 15 08:29:21 jupiter2 dhclient: Sending on   LPF/wlan0/00:16:44:7c:a0:e2
Oct 15 08:29:21 jupiter2 dhclient: Sending on   Socket/fallback
Oct 15 08:29:21 jupiter2 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Oct 15 08:29:21 jupiter2 dhclient: DHCPOFFER of 192.168.0.100 from 192.168.0.1
Oct 15 08:29:21 jupiter2 dhclient: DHCPREQUEST of 192.168.0.100 on wlan0 to 255.255.255.255 port 67
Oct 15 08:29:21 jupiter2 dhclient: DHCPACK of 192.168.0.100 from 192.168.0.1
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>    address 192.168.0.100 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>    prefix 24 (255.255.255.0) 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>    gateway 192.168.0.1 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>    nameserver '192.168.0.1' 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 15 08:29:21 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 15 08:29:21 jupiter2 avahi-daemon[5359]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.100.
Oct 15 08:29:21 jupiter2 dhclient: bound to 192.168.0.100 -- renewal in 290345 seconds.
Oct 15 08:29:21 jupiter2 avahi-daemon[5359]: New relevant interface wlan0.IPv4 for mDNS.
Oct 15 08:29:21 jupiter2 avahi-daemon[5359]: Registering new address record for 192.168.0.100 on wlan0.IPv4.
Oct 15 08:29:22 jupiter2 NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Oct 15 08:29:22 jupiter2 NetworkManager: <info>  Policy set (wlan0) as default device for routing and DNS. 
Oct 15 08:29:22 jupiter2 NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Oct 15 08:29:22 jupiter2 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 15 08:29:22 jupiter2 ntpd[8629]: ntpd exiting on signal 15
Oct 15 08:29:23 jupiter2 ntpdate[10687]: adjust time server 91.189.94.4 offset -0.006663 sec
Oct 15 08:29:23 jupiter2 ntpd[10721]: ntpd 4.2.4p4@1.1520-o Wed Aug 20 17:03:52 UTC 2008 (1)
Oct 15 08:29:23 jupiter2 ntpd[10722]: precision = 1.000 usec



What do you all think? Does this shed more late anywhere!!???

---

### Post by pvroon on 2008-10-15
My RT73usb didn't work anymore either. What I did was proberbly quick and dirty, but it works for me.

I booted the Intrepid install CD and when I reach the desktop mounted my harddrive. I then copied the RT73USB.bin file from the /lib/firmware directory on the live CD to the /lib/firmware directory on the mounted drive. I rebooted and I was back in business.

Hope it works for you.

---

### Post by clarkkent435 on 2008-10-18
Same problem here. Solution: sudo apt-get purge network-manager, restart, then sudo apt-get install network-manager from the 8.10 install CD (or use Synaptic).

This machine was running incremental updates since 8.10 alpha 1; maybe that has something to do with it.

---

### Post by chronographer on 2008-10-24
I'd like to mention for completeness and for future searchers that I can now compile serial monkey's code for the rt73 chipsets (my belkin fsd - 7050 card and a d-link dwl-G122).

If anybody needs a howto then follow this:

```
1.  (remove old drivers)
2. sudo gedit /etc/modprobe.d/blacklist (add the following lines at the end of the file):
blacklist rt73usb
blacklist rt2570
blacklist rt2x00lib
3.sudo apt-get install build-essential
4.sudo apt-get install linux-headers-`uname –r`
5.get the latest version of the driver source from the serialmonkey site. The name is rt73-cvs-daily.tar.gz. I saved it in /usr/src.
6.sudo wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz -O /usr/src/rt73-cvs-daily.tar.gz
7.sudo tar -zxvf rt73-cvs-daily.tar.gz
8.cd /usr/src/rt73*/Module
9.sudo make
10.sudo strip -S rt73.ko (if it’s 2Mb instead of 250Kb ish)
11.sudo make install
12.sudo modprobe rt73
13.sudo gedit /etc/modules – add the text rt73 at the end
14.create text file called rt73 in /etc/modprobe.d  sudo gedit /etc/modprobe.d/rt73
15.put the text “alias wlan0 rt73” in this file
16.rm /etc/modprobe.conf as it’s no longer needed
17.add the following to /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "yourESSID"
pre-up iwconfig wlan0 mode managed
pre-up iwpriv wlan0 set Channel=11
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="your key"
18.reboot/restart network

(note.. I use different /etc/network/interfaces config...)
Hope this helps you get the old wireless up and running
Oh another thing: if you want a link monitor I rate rutilt.

auto wlan0
iface wlan0 inet static
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid TheEther
	pre-up iwconfig wlan0 key C5E90204986D09C602DE18859E
	address 192.168.1.9
	netmask 255.255.255.0
	gateway 192.168.1.1
	wireless-key C5E90204986D09C602DE18859E
	wireless-essid TheEther
	dns-nameservers 192.168.1.1
```

Everything works fine, its been up and running now for a few days! Finally some stable wireless again! Don't forget that if your kernel updates, you will need to recompile and install the module again. (simply the 9th and 11th steps)

---

