---
title: "Ubuntu 11.10, very slow wireless internet"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by Lonium on 2011-10-18
Yesterday I upgraded my Ubuntu-computer from 11.04 to 11.10. Everything looks and works fine, except for the wireless internet which is really slow. My girlfriend still uses 11.04 and she has 11 mbit/s in speed. And the same for my Iphone. But since I upgraded, I only get like 1 mbit/s, which is really frustrating because I can't listen to Spotify and check websites at the same time.

I've googled the same question and I can see that there is other people with pretty much the same problem, but I can't find a solution for it. Can someone help? :p

---

### Post by varunendra on 2011-10-19
To start with, please open a terminal, enter the following commands and post back their outputs here:
```
sudo lshw -C network
ifconfig
iwconfig
cat /etc/network/interfaces
ping -c 4 google.com
```

Please wrap each set of outputs separately in [noparse]```
..and..
```[/noparse] tags. To do so quickly, click on the **#** symbol at the top of edit box. It'll automatically generate the tags, then just copy-paste the output between the tags using your mouse cursor. Doing so preserves formatting and thus makes the output more readable.

---

### Post by pmodin on 2011-10-20
I got the same problem, so I'll hijack this thread :)

```
  *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:de:f1:57:9d:58
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 memory:f3b00000-f3b1ffff memory:f3b2b000-f3b2bfff ioport:7080(size=32)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 88:9f:fa:fd:ae:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.0.0-12-generic firmware=N/A ip=130.229.189.248 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:5000(size=256) memory:f3a00000-f3a03fff
``````
eth0      Link encap:Ethernet  HWaddr f0:de:f1:57:9d:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:19441263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24450058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14397792061 (14.3 GB)  TX bytes:28425586278 (28.4 GB)
          Interrupt:20 Memory:f3b00000-f3b20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2076667 (2.0 MB)  TX bytes:2076667 (2.0 MB)

wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:fd:ae:64  
          inet addr:130.229.189.248  Bcast:130.229.191.255  Mask:255.255.192.0
          inet6 addr: fe80::8a9f:faff:fefd:ae64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:124566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164438621 (164.4 MB)  TX bytes:10127143 (10.1 MB)

``````
wlan0     IEEE 802.11bgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 04:FE:7F:93:9C:E4   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:240   Missed beacon:0

``````
auto lo
iface lo inet loopback

```Ping during network load:```
PING google.com (74.125.43.106) 56(84) bytes of data.
64 bytes from bw-in-f106.1e100.net (74.125.43.106): icmp_req=1 ttl=50 time=42.2 ms
64 bytes from bw-in-f106.1e100.net (74.125.43.106): icmp_req=2 ttl=50 time=870 ms
64 bytes from bw-in-f106.1e100.net (74.125.43.106): icmp_req=3 ttl=50 time=860 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3422ms
rtt min/avg/max/mdev = 42.247/591.356/870.950/388.301 ms
```And no load:```
PING google.com (74.125.43.104) 56(84) bytes of data.
64 bytes from bw-in-f104.1e100.net (74.125.43.104): icmp_req=1 ttl=50 time=24.5 ms
64 bytes from bw-in-f104.1e100.net (74.125.43.104): icmp_req=2 ttl=50 time=23.9 ms
64 bytes from bw-in-f104.1e100.net (74.125.43.104): icmp_req=3 ttl=50 time=27.4 ms
64 bytes from bw-in-f104.1e100.net (74.125.43.104): icmp_req=4 ttl=50 time=23.9 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 23.918/24.957/27.460/1.472 ms
```And lsmod, if that's of interest:```
Module                  Size  Used by
usbhid                 47198  0 
hid                    95463  1 usbhid
parport_pc             36962  0 
dm_crypt               23199  0 
ppdev                  17113  0 
acpi_call              12623  0 
bnep                   18436  2 
rfcomm                 47946  8 
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_conexant    62197  1 
arc4                   12529  2 
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
rtl8192ce              84775  0 
thinkpad_acpi          81819  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               110972  1 rtl8192ce
snd_hda_intel          33390  2 
snd_seq_midi           13324  0 
snd_hda_codec         104802  2 snd_hda_codec_conexant,snd_hda_intel
snd_rawmidi            30547  1 snd_seq_midi
btusb                  18600  2 
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
bluetooth             166112  23 bnep,rfcomm,btusb
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
mac80211              310872  3 rtl8192ce,rtl8192c_common,rtlwifi
psmouse                73882  0 
mei                    41480  0 
serio_raw              13166  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29991  2 snd_seq,snd_pcm
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd                    68266  14 snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
cfg80211              199587  2 rtlwifi,mac80211
nouveau               728662  0 
soundcore              12680  1 snd
tpm_tis                18546  0 
nvram                  14413  1 thinkpad_acpi
ttm                    76805  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
i915                  566711  3 
ahci                   26002  2 
libahci                26861  1 ahci
drm_kms_helper         42558  2 nouveau,i915
firewire_core          63626  1 firewire_ohci
xhci_hcd               78641  0 
sdhci_pci              14032  0 
crc_itu_t              12707  1 firewire_core
sdhci                  32166  1 sdhci_pci
drm                   236330  6 nouveau,ttm,i915,drm_kms_helper
e1000e                160535  0 
i2c_algo_bit           13423  2 nouveau,i915
video                  19412  2 nouveau,i915
```It's a freshly installed 11.10, running on a Lenovo Thinkpad W520.

Any help would be appreciated.

---

### Post by varunendra on 2011-10-20
> **pmodin said:**
> ```
wlan0     IEEE **[COLOR=Red]802.11bgn[/COLOR]**  ESSID:"eduroam"
```
No problem with hijacking, as long as problem is same :)

Given the volume of recent complains about [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250") in Oneiric with N channel, I'd start troubleshooting with this: [http://ubuntuforums.org/showthread.php?p=11360822](http://ubuntuforums.org/showthread.php?p=11360822)

Let's hope this is all you need for the time being.

---

### Post by pmodin on 2011-10-20
Yes, I've seen that bug, however I don't use the iwlagn module, but rtlwifi (that's why I attached lsmod :) )

How do I disable N for rtlwifi? (or where can I see a list of params to pass to modules in general?)

Thanks

---

### Post by varunendra on 2011-10-20
> **pmodin said:**
> Yes, I've seen that bug, however I don't use the iwlagn module, but rtlwifi (that's why I attached lsmod :) )

How do I disable N for rtlwifi? (or where can I see a list of params to pass to modules in general?)

Thanks
Just replace ***iwlagn*** with ***rtl8192ce*** and post back if there is any improvement or none at all.

---

### Post by pmodin on 2011-10-20
> **varunendra said:**
> Just replace ***iwlagn*** with ***rtl8192ce*** and post back if there is any improvement or none at all.```
$ sudo modprobe rtl8192ce 11n_disable=1
FATAL: Error inserting rtl8192ce (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```and dmesg```
[59321.273012] rtl8192ce: Unknown parameter `11n_disable'

```

So how do I disable N for rtlwifi? (or where can I see a list of params to pass to modules in general?).

Thanks

---

### Post by palimmo on 2011-10-20
Same problem with PB Easynote TJ65 and Ubuntu 11.10.
The wifi connection is slower compared to 11.04.... annoying during live video streaming (TV, etc...)

Could you help me, please?
Here some info:

```
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:26:2d:5f:5c:c0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.119 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:f3000000-f300ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 70:1a:04:45:53:c2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.2.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f3100000-f310ffff

```

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:2d:5f:5c:c0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:397638 (397.6 KB)  TX bytes:397638 (397.6 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:45:53:c2  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe45:53c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40743115 (40.7 MB)  TX bytes:9256456 (9.2 MB)

```

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WLAN-7BCE36"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 04:C0:6F:DA:7B:CE   
          Bit Rate=162 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0

```

```
~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
~$ ping -c 4 google.com
PING google.com (209.85.148.105) 56(84) bytes of data.
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=1 ttl=57 time=61.5 ms
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=2 ttl=57 time=60.4 ms
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=3 ttl=57 time=62.1 ms
64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=4 ttl=57 time=61.4 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 60.413/61.358/62.104/0.655 ms

```

Should I disable the N connection? How?
Thanks a lot!!

---

### Post by varunendra on 2011-10-20
> **pmodin said:**
> ```
$ sudo modprobe rtl8192ce 11n_disable=1
FATAL: Error inserting rtl8192ce (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko): **Unknown symbol in module, or unknown parameter** (see dmesg)

```Ah, my mistake. I took a shot in the dark only to realize there is no such parameter at all for your driver. Will look further to see what else is possible. Right now I have no reliable ideas.


@palimmo,
Please try the following and tell us if it makes any difference:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```If it improves things, we'll then need to make it permanent, but first let's see if it works.

---

### Post by palimmo on 2011-10-20
> **varunendra said:**
> Ah, my mistake. I took a shot in the dark only to realize there is no such parameter at all for your driver. Will look further to see what else is possible. Right now I have no reliable ideas.


@palimmo,
Please try the following and tell us if it make any difference:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up
```

If it improves things, we'll then need to make it permanent, but first let's see if it works.

Should i reboot after this changes or only disconnect/reconnect?

---

### Post by varunendra on 2011-10-20
> **palimmo said:**
> Should i reboot after this changes or only disconnect/reconnect?
Reboot is not required after following those steps. (in fact reboot will neutralize the changes unless we make it permanent).

---

### Post by palimmo on 2011-10-20
> **varunendra said:**
> Reboot is not required after following those steps. (in fact reboot will neutralize the changes unless we make it permanent).

Ok.. 
I' ve tried before a reboot.... and after.
But I haven't noticed improvements.
I've tried also this command
```
sudo -s
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf

```
(is it more or less the same?) and reboot.... 
But nothing. :(

---

### Post by palimmo on 2011-10-20
Well...
probably it's better to have a my own thread
[http://ubuntuforums.org/showthread.php?t=1866335](http://ubuntuforums.org/showthread.php?t=1866335)

I don't want to steal space here..

---

### Post by palimmo on 2011-10-21
editing..sorry

---

### Post by palimmo on 2011-10-21
editing..sorry

---

### Post by heke on 2011-10-21
Well, I'm not the only one with a very slow wireless... 

I've been quite satisfied with the ubuntu 11.04, but after the 11.10 uppgrade  certainly rather not. This slowness persists even with xfce desktop, the gnome shell (that one I wouldn't use anyway) and the fallback gnome desktop.

Normally I use the tor anonymizing service now and then, but this present slowness actually makes it impossible (connection timed out error).

I will not make a clean reinstallation of 11.04, nor do I actually ask or expect anyone being able to help, just pouring out my frustration.

UPDATE 23.10.11:

The problem is with a USB wireless dongle DLINK DWL-G122  B1 ver. 2.03. With this device the wifi runs indeed very slowly. I don't know why.  My solution ist to discard that dongle for the time being and use other means of wireless connection until some ubuntu update returns the speed to the DWL dongle. With the other means, and with the fallback gnome classic desktop, the browsing speed seems to be as I was used to with 11.04.

Thus, my previous frustration is now less.

---

### Post by varunendra on 2011-10-21
@*pmodin* and *palimmo*,
Before suggesting anything further, I should clarify that I have no first hand experience with these wifi devices and even my theoretical knowledge about them is terribly limited.

Having said this, the drivers you both currently have in use seem to be the only suitable drivers for your devices, and as per the outputs you both have provided, they seem to be working as fine as they can (are connected and working, no connection drops, no packet drops, nor any other common errors in ifconfig). Unlike the intel drivers, there are no such parameters associated with your drivers which can allow us to experiment with disabling of the suspected N channel. Accordingly, there are only a few more things you may try:

[LIST]
[*]If you have access to your router, please try selecting b/g mode only to see if it is related with the infamous N-channel bug at all.
[*]Try disabling IPv6 on your interfaces as per [this]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html") or [this]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") guide. Although I seriously doubt it has anything to do with your problems since it was working fine on Natty.
[*]As a last resort (which 'should' work) would be to try installing and using an older kernel in Oneiric (from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")) until the issue is fixed in the newer kernel.
[/LIST]
For now, this is all I could come up with, maybe an expert with more knowledge can suggest something better.



**_PS_:**
@*palimmo*,
I see that you are creating three copies of each of your posts (including one at your own thread [here]("http://ubuntuforums.org/showthread.php?t=1866335")). This not only dilutes the community efforts, but also wastes server space and confuses the helpers as to where to respond. As such, it may also be frowned upon by the mods. You are already getting better help from 'wildmanne39', one of the best networking experts around here, in [this]("http://ubuntuforums.org/showthread.php?t=1859151&page=5") thread. Accordingly, I would request you to to please create all your posts with details at one place (obviously in your own thread now that it is created), and edit all your other posts at other places to remove all the duplicate text there and instead change them to only links to your detailed posts.

This way, all the helpers interested in helping with your problem will be directed to one place, thus providing you best possible help with minimum wastage of time and resources. (you see, trying out two different suggestions without mutual understanding may sometimes be a perfect recipe for disaster). Please make this a habit as it is in your own best interest.


@*heke*,
If you have an intel wifi card, please try the solution suggested in the link in post #4. Although you have clearly stated that you are "just pouring out your frustration" :), I would suggest that if your problem is unsolved, you should create your own thread with this issue and post all the relevant details there. Even if it couldn't get you a direct solution, a number of such 'unsolved' threads may help getting the attention of the developers/experts, thus representing an urgent need for fixing this issue.

---

### Post by palimmo on 2011-10-22
> **varunendra said:**
> @*pmodin* and *palimmo*,
Before suggesting anything further, I should clarify that I have no first hand experience with these wifi devices and even my theoretical knowledge about them is terribly limited.

Having said this, the drivers you both currently have in use seem to be the only suitable drivers for your devices, and as per the outputs you both have provided, they seem to be working as fine as they can (are connected and working, no connection drops, no packet drops, nor any other common errors in ifconfig). Unlike the intel drivers, there are no such parameters associated with your drivers which can allow us to experiment with disabling of the suspected N channel. Accordingly, there are only a few more things you may try:

[LIST]
[*]If you have access to your router, please try selecting b/g mode only to see if it is related with the infamous N-channel bug at all.
[*]Try disabling IPv6 on your interfaces as per [this]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html") or [this]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") guide. Although I seriously doubt it has anything to do with your problems since it was working fine on Natty.
[*]As a last resort (which 'should' work) would be to try installing and using an older kernel in Oneiric (from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")) until the issue is fixed in the newer kernel.
[/LIST]
For now, this is all I could come up with, maybe an expert with more knowledge can suggest something better.



**_PS_:**
@*palimmo*,
I see that you are creating three copies of each of your posts (including one at your own thread [here]("http://ubuntuforums.org/showthread.php?t=1866335")). This not only dilutes the community efforts, but also wastes server space and confuses the helpers as to where to respond. As such, it may also be frowned upon by the mods. You are already getting better help from 'wildmanne39', one of the best networking experts around here, in [this]("http://ubuntuforums.org/showthread.php?t=1859151&page=5") thread. Accordingly, I would request you to to please create all your posts with details at one place (obviously in your own thread now that it is created), and edit all your other posts at other places to remove all the duplicate text there and instead change them to only links to your detailed posts.

This way, all the helpers interested in helping with your problem will be directed to one place, thus providing you best possible help with minimum wastage of time and resources. (you see, trying out two different suggestions without mutual understanding may sometimes be a perfect recipe for disaster). Please make this a habit as it is in your own best interest.


@*heke*,
If you have an intel wifi card, please try the solution suggested in the link in post #4. Although you have clearly stated that you are "just pouring out your frustration" :), I would suggest that if your problem is unsolved, you should create your own thread with this issue and post all the relevant details there. Even if it couldn't get you a direct solution, a number of such 'unsolved' threads may help getting the attention of the developers/experts, thus representing an urgent need for fixing this issue.

Thanks Varunendra. I will try soon with your suggestions.

Regarding my posts.. you're right.
I decide too late to open a my own thread.
I will edit all the others and insert a link to my own.

I'm sorry.... thank you again.
I'll let you know what happens with your suggestions...  
In my thread, of course! :)

[http://ubuntuforums.org/showthread.php?t=1866335](http://ubuntuforums.org/showthread.php?t=1866335)

---

