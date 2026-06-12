---
title: "Wireless (ath5k) stopped working"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by augie777 on 2009-04-10
Hi, I'm running Jaunty (9.04 beta) because the support for my wireless card is missing in 8.10. It's worked great for a couple of weeks until yesterday morning (after a nights suspend - as usual). The system acts as if the signal is non-existent, but it is there all right. Other XP and Linux boxes works fine. First time I inserted the wired network - the wireless also came back up! But this "work-around" only worked once. When I first installed the system I tried the madwifi driver, without success. Please, help :)

Box: Compaq Presario CQ60 (april-09)

```

micke@MyCompaq:~$ uname -a
Linux MyCompaq 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:39:23 UTC 2009 x86_64 GNU/Linux
micke@MyCompaq:~$ lsb_release -d
Description:	Ubuntu jaunty (development branch)
micke@MyCompaq:~$ 

```

```
micke@MyCompaq:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```

micke@MyCompaq:~$ lspci
...
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
```

micke@MyCompaq:~$ cat /etc/modprobe.d/blacklist
cat: /etc/modprobe.d/blacklist: No such file or directory

```
```

micke@MyCompaq:~$ lsmod | grep ath
ath5k                 116224  0 
mac80211              251144  1 ath5k
led_class              13064  1 ath5k
cfg80211               43168  2 ath5k,mac80211

```
```

micke@MyCompaq:~$ lshw
...
          *-network
                description: Wireless interface
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 01
                serial: 00:23:4d:b0:ec:d3
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

---

### Post by t0mppa on 2009-04-10
The older HAL-based MadWifi driver has worked for a lot of people with the same wireless chip, at least on 8.10. From what I gathered from the their website, the ath5k is still a work in progress (could be wrong though).

If you want give it a try and need help setting it up, see: [http://ubuntuforums.org/showthread.php?t=1120259]("http://ubuntuforums.org/showthread.php?t=1120259")

---

### Post by augie777 on 2009-04-10
t0mppa, thanks for your reply. I've installed the madwifi driver as described in your other thread but still no wireless. I'm not very good at this but it seems like the other driver also loads:
```

micke@MyCompaq:~$ cat /etc/modules
lp
rtc
ath_pci

```
```

micke@MyCompaq:~$ lsmod | grep ath
ath_pci               225344  0 
wlan                  259360  1 ath_pci
ath_hal               339216  1 ath_pci
ath5k                 116224  0 
mac80211              251144  1 ath5k
led_class              13064  1 ath5k
cfg80211               43168  2 ath5k,mac80211

```
```

micke@MyCompaq:~$ dmesg | grep ath
[    3.944862] device-mapper: multipath: version 1.0.5 loaded
[    3.944865] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.217860] ath5k_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.217875] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   12.217942] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   12.419319] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```

---

### Post by t0mppa on 2009-04-10
Figured it might come down to both of them vying for control. In that case, you'll have to try blacklisting the ath_5k.

You can do that by opening up the black list file ```
gksudo gedit /etc/modprobe.d/blacklist
``` and then adding the module(s) into the list.

After that's done, will have to still disable it from kernel:```
sudo modprobe -r ath5k
```

---

### Post by Xbehave on 2009-04-10
It's best to figure out which works before messing around with /etc/modprobe.d/blacklist
(on ubuntu there may be /etc/modprobe.d/madwifi ) which makes it easy to switch between the two once you figure it out

```
sudo modprobe -r ath5k ; sudo modprobe ath_pci
```

unfortunatly the way to switch from madwifi to ath5k is abit more complicated, you have to removed the madwifi modules in the correct order
```
lsmod | grep ath
``` will help but once you get the right order  you can remove them with a command **like **:

```
rmmod ath_pci ; rmmod ath_rate_sample ; rmmod ath_hal ; modprobe ath5k 
```

---

### Post by augie777 on 2009-04-11
Thanks th0mppa and Xbehave! I tried your suggestions but the wireless is dead
```

micke@MyCompaq:/etc/modprobe.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```
I blacklisted ath5k in blacklist.conf, and rebooted. 
```

micke@MyCompaq:/etc/modprobe.d$ dmesg | grep  ath
[    3.936856] device-mapper: multipath: version 1.0.5 loaded
[    3.936858] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.977400] ath_pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.977415] ath_pci 0000:03:00.0: setting latency timer to 64
[   13.471421] MadWifi: ath_attach: Switching rfkill capability off.
[   13.489791] ath_pci: wifi0: Atheros 5424/2424: mem=0xd5100000, irq=17
[   39.020048] ath0: no IPv6 routers present

```
```

micke@MyCompaq:/etc/modprobe.d$ lsmod | grep ath
ath_rate_sample        22400  1 
ath_pci               225344  0 
wlan                  259360  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               339216  3 ath_rate_sample,ath_pci

```

---

### Post by t0mppa on 2009-04-11
Browsing some of the solutions, I found out that MadWifi guys gave some nice little scripts for clearing all your old drivers out of the way before installing new ones. So, I'd try with using them first and then trying once more to install from a clean plate. Also do disable any Atheros drivers Hardware Drivers (under System / Administration) might be showing up.

You'll find the scripts by going to the scripts directory inside the directory you unpacked from the package you downloaded (madwifi-hal-0.10.5.6-current.tar.gz).

```
$ sudo ./madwifi-unload
$ sudo ./find-madwifi-modules.sh $(uname -r)
```

And if things still don't work, those should help you clear things up before trying something else as well.

---

