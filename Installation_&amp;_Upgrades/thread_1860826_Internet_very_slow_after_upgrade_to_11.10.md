---
title: "Internet very slow after upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by room271 on 2011-10-15
Hi all,

I have a Dell m14x laptop, dual-booting Windows and Ubuntu.

After upgrading to 11.10 the wireless (have no cable to test a straight connection) internet is very slow. It connects fine and shows a good speed in the info box, but in Firefox pages take ages (30s at least) to load. Ubuntu software (Chromium) has also failed to install because of connection problems.

The Wireless worked great before the upgrade, and is working great now for Windows so I know it is something to do with the upgrade process.

I've tried searching in the forum and asked on IRC but no luck.

Any help appreciated!

Nic

---

### Post by varunendra on 2011-10-17
Hi Nic, and welcome to the forums!

Can you pleas open a terminal and post outputs of the following commands:
```
sudo lshw -C network
ifconfig -a
iwconfig
lsmod
cat /etc/network/interfaces
ping -c 4 google.com
```While posting the outputs, click on the **#** symbol at the top of edit box to generate [noparse]```
[/noparse].... *(paste your output here)* ....[noparse]
```[/noparse] tags, then copy-paste the output in between the generated tags. Paste each set of outputs in separate tag sets. Doing this preserves the formatting of the outputs and ensures better readability.

---

### Post by galgamo on 2011-10-17
Hi!!  I have a very similar problem upgrading from 10.10 to 11.04  In my case i used a wired connection. My network card has a realtek chipset.  I experienced low speed. I tried reverting back to the older driver (from r8169 to r8168) and it solved the issue.  I hope this works for you too.  Bye!!

---

### Post by compaddict on 2011-10-17
Same problem I had. HP DV7. Subscribed...
 
> **room271 said:**
> Hi all,
 
I have a Dell m14x laptop, dual-booting Windows and Ubuntu.
 
After upgrading to 11.10 the wireless (have no cable to test a straight connection) internet is very slow. It connects fine and shows a good speed in the info box, but in Firefox pages take ages (30s at least) to load. Ubuntu software (Chromium) has also failed to install because of connection problems.
 
The Wireless worked great before the upgrade, and is working great now for Windows so I know it is something to do with the upgrade process.
 
I've tried searching in the forum and asked on IRC but no luck.
 
Any help appreciated!
 
Nic

---

### Post by room271 on 2011-10-17
[FONT=monospace]Hey, thanks for the replies. Here is the info requested...

sudo lshw -C network:

[/FONT]```
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: c0
       serial: 5c:26:0a:4b:6c:8c
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:53 memory:d9800000-d983ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:88:bc:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=39.31.5.1 build 35138 ip=192.168.0.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:d8800000-d8801fff

```
[FONT=monospace]
ifconfig -a:

[/FONT]```
eth0      Link encap:Ethernet  HWaddr 5c:26:0a:4b:6c:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:53 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:88:bc:1e  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::8ea9:82ff:fe88:bc1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1304903 (1.3 MB)  TX bytes:182393 (182.3 KB)

```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"freebox"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 26:F6:1B:74:07:90   
          Bit Rate=121.5 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:626  Invalid misc:153   Missed beacon:0

```
[FONT=monospace]
lsmod:

[/FONT]```
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  1 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
arc4                   12529  2 
dell_wmi               12681  0 
snd_hda_intel          33390  2 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314213  0 
mac80211              310872  1 iwlagn
rts_pstor             445246  0 
cfg80211              199587  2 iwlagn,mac80211
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
i915                  566711  3 
nouveau               728662  0 
ttm                    76805  1 nouveau
xhci_hcd               78641  0 
drm_kms_helper         42558  2 i915,nouveau
drm                   236330  6 i915,nouveau,ttm,drm_kms_helper
ahci                   26002  2 
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
libahci                26861  1 ahci
i2c_algo_bit           13423  2 i915,nouveau
mxm_wmi                12979  1 nouveau
atl1c                  41643  0 
wmi                    19256  2 dell_wmi,mxm_wmi
vesafb                 13809  0 
video                  19412  2 i915,nouveau

```

cat /etc/networks/interfaces:

```
auto lo
iface lo inet loopback

```

ping -c 4 google.com

```
PING google.com (209.85.148.99) 56(84) bytes of data.
64 bytes from fra07s07-in-f99.1e100.net (209.85.148.99): icmp_req=1 ttl=53 time=60.8 ms
64 bytes from fra07s07-in-f99.1e100.net (209.85.148.99): icmp_req=2 ttl=53 time=49.5 ms
64 bytes from fra07s07-in-f99.1e100.net (209.85.148.99): icmp_req=3 ttl=53 time=42.3 ms
64 bytes from fra07s07-in-f99.1e100.net (209.85.148.99): icmp_req=4 ttl=53 time=39.8 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 39.880/48.157/60.872/8.153 ms

```

---------

Hopefully this is useful! Thanks again,

nicl

---

### Post by varunendra on 2011-10-18
Nothing seems abnormal to me except this:> **room271 said:**
> iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE [COLOR=Red]**802.11bgn**[/COLOR]  ESSID:"freebox"
....
....

```
which is also normal for other kernels, but apparently there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/836250") in Oniric related with N-channel which might be affecting you too. Accordingly, please try the following:
```
sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1
```Then start browsing and see if there is improvement. If there is, then make this change permanent by creating an 'options' file:
```
gksu gedit /etc/modprobe.d/options.conf
```Add this line to the file:
```
options iwlagn 11n_disable=1
```proofread, save and exit.



**_EDIT_:**
Just for clarification, the above steps would disable N-channel support on the card. So it is not a solution, but just a workaround to get full speeds at other channels, until the bug is actually fixed in newer kernel/updates. Those who have applied this workaround may want to keep an eye on the above linked bug-report page to see when a fix is released. (It has got 'High Importance', so we may expect it soon).

---

### Post by room271 on 2011-10-18
Hi Varun,

thanks for this. It works ;) Hopefully a driver update or whatever is the more permanent solution will be added as an update down the line. But for now I can finally use 11.10 - which is great!

Thanks,

nicl

---

### Post by dydimus on 2011-10-18
Thank you for this solution, I was looking for a fix like this one and now my wireless goes as fast as it should go.
Thank you!

---

### Post by varunendra on 2011-10-18
Nice to hear it worked. Thanks to both of you for the confirmation. However, all credits should go to *wildmanne39* whose [post]("http://ubuntuforums.org/showpost.php?p=11350040&postcount=21") I stole this solution from ;)


@galgamo,
The r8168 driver is associated with gigabit ethernet interface, not a wireless one. Also, the normal solution, i.e., the normal combination of r8168 driver + RTL8168B card works only for kernels older than 3.x.x. For kernel 3 onwards, it requires some more tweaking. Just for your info :)

---

### Post by mukanya on 2011-10-19
Thanks. You saved me hours.

---

### Post by youngmit on 2011-10-21
Any hope of an updated driver that can handle the 802.11n features? At least from what i can tell, this solution would preclude us from using n networks. :-(

[edit] ...or at least from taking advantage of the n-ness of the network.

---

### Post by varunendra on 2011-10-22
> **youngmit said:**
> Any hope of an updated driver that can handle the 802.11n features? At least from what i can tell, this solution would preclude us from using n networks. :-(

[edit] ...or at least from taking advantage of the n-ness of the network.
As included in my 'Edit', my hopes are high since the bug has got 'High Importance', but am not familiar with the pace of developers, so can't tell how many weeks or months this "soon" would mean ;). Also, as much as I understand, this is not a problem with the driver, but the kernel itself. So it should be a kernel update that should be able to really solve the problem. For now, you may try installing an older kernel ([from here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")) to get the N-channel support, but I haven't got any confirmations yet about whether it is a good idea.


**_Edit_:**
IMHO, it would be better to stick with Natty rather than trying an older kernel on Oneiric, if you really need N-channel support. You can switch to Oneiric later when it gets fixed.

---

