---
title: "Asus wifi disabled"
date: 2016-04-30
forum: MINT
---

### Post by Joleen on 2016-04-30
Dear all
my 6 year old asus eee pc netbook running mint now, suddenly decided to hardblock forever  the wifi. When I push the hardware buttons -fn+f2 or the little switch-  and then list rfkill, it is obvious that these buttons, only affect soft  blocks on and off. I don't know why...
something like this has also affected ubuntu users -see this thread [http://ubuntuforums.org/showthread.php? ... t13158359-]("http://ubuntuforums.org/showthread.php?t=2181558&page=5&p=13158359&highlight=asus_wmi#post13158359-") but the workaround does not work for me
.I normally have put the netbook to retirement after it crashed two years ago , because the hardware is really tired, but needed it for a professional trip...So I need the wireless badly...
so:

maria@bouncereturns ~ $ lsmod | grep -e bcma-pci-bridge -e asus
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
video                  18903  2 i915,asus_wmi
wmi                    18673  1 asus_wmi


I saw that this asus_wmi thing is running. So I tried the echo options thing you wrote, and salvated all these people, altering the asus_wmi for me:
maria@bouncereturns ~ $ sudo -i
[sudo] password for maria: 
bouncereturns ~ # echo "options asus_wmi wlan_status=1" > /etc/modprobe.d/asus_wmi.conf
bouncereturns ~ # modprobe -r asus_wmi
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/asus.conf line 1: ignoring bad line starting with 'options_asus_wmi'
modprobe: FATAL: Module asus_wmi is in use.
bouncereturns ~ # modprobe asus_wmi
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/asus.conf line 1: ignoring bad line starting with 'options_asus_wmi'
bouncereturns ~ # exit


as you can see, something is going wrong. thanks so much for your time...

---

### Post by chili555 on 2016-04-30
> **Joleen said:**
> oh, forgot to mention that I also used the default command with which you started this thread (echo....asus_nb_wmi....) and did not work. Thank you again :roll:It won't work because* asus_nb_wmi* isn't loaded as per your lsmod above.> ignoring bad line starting with 'options_asus_wmi'
modprobe: FATAL: Module asus_wmi is in use.Please run:```
modinfo asus_wmi
```On my admittedly non-Mint machine, it returns:```
filename:       /lib/modules/4.4.6-040406-generic/kernel/drivers/platform/x86/asus-wmi.ko
license:        GPL
description:    Asus Generic WMI Driver
author:         Corentin Chary <corentin.chary@gmail.com>, Yong Wang <yong.y.wang@intel.com>
srcversion:     EFA91F0D921AF2FFC96749F
depends:        sparse-keymap,wmi,video
intree:         Y
vermagic:       4.4.6-040406-generic SMP mod_unload modversions 

```We see no manipulable parameters there. Compare:```
chili@T440p:~$ [COLOR="#FF0000"]modinfo asus_nb_wmi[/COLOR]
filename:       /lib/modules/4.4.6-040406-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
alias:          wmi:0B3CBB35-E3C2-45ED-91C2-4C5A6D195D1C
license:        GPL
description:    Asus Notebooks WMI Hotkey Driver
author:         Corentin Chary <corentin.chary@gmail.com>
srcversion:     3C571A40D6EF5CE0EC109E8
depends:        asus-wmi
intree:         Y
vermagic:       4.4.6-040406-generic SMP mod_unload modversions 
[COLOR="#FF0000"]parm:           wapf[/COLOR]:WAPF value (uint)

```Now, whether asus_wmi or else asus_nb_wmi gets called and used depends on the exact make and model of your laptop. It would do no good to try to load the wrong module; i.e., asus_nb_wmi. 

We don't know much about Mint and we suggest you ask here: [https://forums.linuxmint.com/](https://forums.linuxmint.com/)

---

### Post by jeremy31 on 2016-04-30
*Thread moved to **MINT**.*

Please post results for ```
lsmod
```

Also post the model of this machine

---

### Post by Joleen on 2016-05-01
Dear Jeremy
here is the output you asked for
```

maria@bouncereturns ~ $ lsmod
Module                  Size  Used by
joydev                 17101  0 
arc4                   12536  2 
rfcomm                 53664  8 
bnep                   18895  2 
binfmt_misc            13140  1 
brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
eeepc_wmi              12983  0 
b43                   356470  0 
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
mac80211              545990  2 b43,brcmsmac
cfg80211              409394  3 b43,brcmsmac,mac80211
ssb                    51854  1 b43
snd_hda_codec_realtek    51029  1 
snd_hda_intel          42730  3 
snd_hda_codec         164067  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
videobuf2_memops       13170  1 videobuf2_vmalloc
videobuf2_core         39258  1 uvcvideo
videodev              108503  2 uvcvideo,videobuf2_core
dm_multipath           22402  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
scsi_dh                14458  1 dm_multipath
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
coretemp               13195  0 
psmouse                91033  0 
btusb                  27580  0 
lpc_ich                16864  0 
serio_raw              13230  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
bluetooth             342263  22 bnep,btusb,rfcomm
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
bcma                   42043  3 b43,brcmsmac
snd                    60871  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
mac_hid                13037  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
dm_mirror              21756  0 
dm_region_hash         20121  1 dm_mirror
dm_log                 18072  2 dm_region_hash,dm_mirror
i915                  705396  2 
i2c_algo_bit           13197  1 i915
drm_kms_helper         46907  1 i915
ahci                   25579  3 
drm                   243792  3 i915,drm_kms_helper
libahci                26754  1 ahci
atl1c                  40949  0 
video                  18903  2 i915,asus_wmi
wmi                    18673  1 asus_wmi

```

and Dr. Chili, this is the output you asked for
```
maria@bouncereturns ~ $ modinfo asus_wmi
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/platform/x86/asus-wmi.ko
license:        GPL
description:    Asus Generic WMI Driver
author:         Corentin Chary <corentin.chary@gmail.com>, Yong Wang <yong.y.wang@intel.com>
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

```



either looks strangely like your output on a machine not running asus_wmi, or I am tired.
Thank you all for your time and sorry for posting here, but many times I have been helped in mint with ubuntu coding...I ll post in mint forums too..aaaaaah, damned asus.

---

### Post by jeremy31 on 2016-05-01
Don't see anything strange in the results.  Please use code tags when posting terminal output, I see Irihapeti has added them for you in those posts

See the wireless script link in my signature and post the results from the wireless-info.txt file using the code tags.

---

### Post by Joleen on 2016-05-02
> **jeremy31 said:**
> Don't see anything strange in the results.  Please use code tags when posting terminal output, I see Irihapeti has added them for you in those posts

See the wireless script link in my signature and post the results from the wireless-info.txt file using the code tags.

Hello.
It seems that the wireless info text is too long to be posted. -I tried using code tags - I think. So I attach it.

---

### Post by jeremy31 on 2016-05-02
This may work as there is an error in the dmesg part of the report
```
echo "options eeepc_wmi hotplug_wireless=Y" | sudo tee /etc/modprobe.d/eeepc.conf
```

And we should remove the invalid parameter setting for asus_wmi

```
sudo rm /etc/modprobe.d/asus.conf
```

Reboot

---

### Post by Joleen on 2016-05-02
wait, no. Now I did it right.

```
########## wireless info START ##########

Report from: 02 May 2016 12:16 EEST +0300

Booted last: 02 May 2016 12:10 EEST +0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:   LinuxMint
Description:   Linux Mint 17 Qiana
Release:   17
Codename:   qiana

##### kernel ############################

Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
   Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
   Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
   Subsystem: AzureWave Device [1a3b:2047]
   Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 001 Device 002: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 13d3:3315 IMC Networks Bluetooth module
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
   Soft blocked: no
   Hard blocked: no
1: asus-wlan: Wireless LAN
   Soft blocked: no
   Hard blocked: no
2: asus-bluetooth: Bluetooth
   Soft blocked: no
   Hard blocked: no
3: phy0: Wireless LAN
   Soft blocked: no
   Hard blocked: yes

##### lsmod #############################

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356470  0 
mac80211              545990  2 b43,brcmsmac
eeepc_wmi              12983  0 
cfg80211              409394  3 b43,brcmsmac,mac80211
asus_wmi               23495  1 eeepc_wmi
sparse_keymap          13708  1 asus_wmi
ssb                    51854  1 b43
bcma                   42043  3 b43,brcmsmac
video                  18903  2 i915,asus_wmi
wmi                    18673  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4215 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:8690424 (8.6 MB)  TX bytes:439004 (439.0 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

   NetworkManager

Running:

root       778     1  0 12:10 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC address>,<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/orange]] (600 root)
[connection] id=orange | type=802-11-wireless
[802-11-wireless] ssid=orange | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/conn-x91c9a0]] (600 root)
[connection] id=conn-x91c9a0 | type=802-11-wireless
[802-11-wireless] ssid=conn-x91c9a0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/conn-x91c9a0 1]] (600 root)
[connection] id=conn-x91c9a0 1 | type=802-11-wireless
[802-11-wireless] ssid=conn-x91c9a0 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/GreenRoom]] (600 root)
[connection] id=GreenRoom | type=802-11-wireless
[802-11-wireless] ssid=GreenRoom | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/OTEfa1908]] (600 root)
[connection] id=OTEfa1908 | type=802-11-wireless
[802-11-wireless] ssid=OTEfa1908 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wind WiFi pZdqXx]] (600 root)
[connection] id=Wind WiFi pZdqXx | type=802-11-wireless
[802-11-wireless] ssid=Wind WiFi pZdqXx | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CYTA 50B8]] (600 root)
[connection] id=CYTA 50B8 | type=802-11-wireless
[802-11-wireless] ssid=CYTA 50B8 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/OTE WiFi Fon]] (600 root)
[connection] id=OTE WiFi Fon | type=802-11-wireless
[802-11-wireless] ssid=OTE WiFi Fon | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/katina]] (600 root)
[connection] id=katina | type=802-11-wireless
[802-11-wireless] ssid=katina | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LAB]] (600 root)
[connection] id=LAB | type=802-11-wireless
[802-11-wireless] ssid=LAB | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOL_ZTE_4]] (600 root)
[connection] id=HOL_ZTE_4 | type=802-11-wireless
[802-11-wireless] ssid=HOL_ZTE_4 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KTEL ACHAIAS 136]] (600 root)
[connection] id=KTEL ACHAIAS 136 | type=802-11-wireless
[802-11-wireless] ssid=KTEL ACHAIAS 136 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOKIA Lumia 625_1291]] (600 root)
[connection] id=NOKIA Lumia 625_1291 | type=802-11-wireless
[802-11-wireless] ssid=NOKIA Lumia 625_1291 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Xperia M2_adef]] (600 root)
[connection] id=Xperia M2_adef | type=802-11-wireless
[802-11-wireless] ssid=Xperia M2_adef | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hhonors-public]] (600 root)
[connection] id=hhonors-public | type=802-11-wireless
[802-11-wireless] ssid=hhonors-public | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KTEL ACHAIAS 117]] (600 root)
[connection] id=KTEL ACHAIAS 117 | type=802-11-wireless
[802-11-wireless] ssid=KTEL ACHAIAS 117 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Athens (based on set time zone)

country US:
   (2402 - 2472 @ 40), (3, 27)
   (5170 - 5250 @ 40), (3, 17)
   (5250 - 5330 @ 40), (3, 20), DFS
   (5490 - 5600 @ 40), (3, 20), DFS
   (5650 - 5710 @ 40), (3, 20), DFS
   (5735 - 5835 @ 40), (3, 30)
   (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     E41B811D88783DD5BC38565
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/asus.conf]
options_asus_wmi wafp=4

[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=4

[/etc/modprobe.d/asus_wmi.conf]
options asus_wmi wlan_status=1

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0'  [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>",  ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[   23.333319] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   24.333439] bcma-pci-bridge 0000:02:00.0: no hotplug settings from platform (repeated 2 times)
[   27.987601] brcmsmac bcma0:0: brcms_ops_start: brcms_up() returned -132
[   28.004498] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.038157] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[   41.851815] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[   43.483244] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  143.575575] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[  148.206279] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  148.526511] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  148.526540] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  170.708572] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[  173.004189] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  191.092651] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Down
[  192.664987] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>

########## wireless info END ############
```

I runned the commands and rebooted, problem persists. Thanks Jeremy.


ah, the model is eee pc seashell series.

```
System Information
        Manufacturer: ASUSTeK Computer INC.
        Product Name: 1015PEM
        Version: x.x
        Serial Number: B1OABC081095
        UUID: 63205141-7890-4251-8586-BCAEC5A31EC2
        Wake-up Type: Power Switch
        SKU Number: 1015PEM
        Family: Eee PC
``` 
and sub-model and disk is ```
maria@bouncereturns ~ $ sudo dmidecode | less | grep Version
[sudo] password for maria: 
    Version: 0903   
    Version: x.x
    Version: x.xx
    Version: x.x
    Version: Intel(R) Atom(TM) CPU N550   @ 1.50GHz
```

---

### Post by jeremy31 on 2016-05-02
We could blacklist asus_wmi ```
echo "blacklist asus_wmi" | sudo tee /etc/modprobe.d/asus_wmi.conf
```
Reboot

---

### Post by Joleen on 2016-05-02
> **jeremy31 said:**
> We could blacklist asus_wmi ```
echo "blacklist asus_wmi" | sudo tee /etc/modprobe.d/asus_wmi.conf
```
Reboot

No effect. I have also tried to remove it by adding a blacklist line the blacklist list, using ```
sudo nano /etc/modprobe.d/blacklist.conf
```, but neither this had any effect.

---

### Post by jeremy31 on 2016-05-02
You can try going into BIOS and reset to defaults.  A trick that works on Toshibas, is to shut down, remove battery and power cord and press the power button for 10 seconds

If nothing else the tape trick should work

---

### Post by Joleen on 2016-05-02
> **jeremy31 said:**
> You can try going into BIOS and reset to defaults.  A trick that works on Toshibas, is to shut down, remove battery and power cord and press the power button for 10 seconds

If nothing else the tape trick should work

oh God, it WAS blocked from within the BIOS. I did not even had to reset: there was this WLAN thing in the bios marked as "disabled", marked it "enabled" and everything works now. I am really sorry for taking up your time, I should have checked BIOS first...since it was suggested in topics here, too! I feel like an idiot!
thank you Jeremy,
administration moved me in this thread so I cannot mark it as solved myself.
thanks again.

---

### Post by jeremy31 on 2016-05-02
I moved it here and I will see if I can mark it as solved.  Glad to help

You are likely not seeing any activity on your question in Linux Mint forum because I am doing that here and do not feel like posting the same thing on 2 forums

Edit: Marked as Solved

If I disable my WLAN on my Lenovo, it doesn't show up in lspci results as if it doesn't exist or was removed from the laptop

---

### Post by Joleen on 2016-05-02
hahah and I was wondering! but i marked it as solved there! thanks!!!

---

