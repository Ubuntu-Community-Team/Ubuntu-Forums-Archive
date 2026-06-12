---
title: "MSi Wireless Issues, wont detect wireless card ( Qualcomm Atheros AR8161 Gigabit )"
date: 2015-12-20
forum: MINT
---

### Post by allen17 on 2015-12-20
I'm a complete noob and am having issues detecting my wireless card. I  have tried older solutions posted on this forum and other places but when i try to  compile their provided code it leads to a bunch of errors. i am able to  fix a few of the errors but can't get rid of it all. 
My current laptop is the MSI PE60 6QE-031US. Has anyone else faced this issue? if so, is there a solution? please help!

Note: USB Tethering with my smart phone works and old USB adapter works fine.

Thanks in advance.


```

########## wireless info START ##########

Report from: 20 Dec 2015 17:33 CST -0600

Booted last: 20 Dec 2015 17:30 CST -0600

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 3.19.0-32-generic #37~14.04.1-Ubuntu SMP Thu Oct 22 09:41:40 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/preseed/linuxmint.seed, cdrom-detect/try-usb=true, persistent, noprompt, floppy.allowed_drive_mask=0, ignore_uuid, boot=casper, iso-scan/filename=, quiet, splash, --

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Device [8086:3165] (rev 81)
    Subsystem: Intel Corporation Device [8086:4010]

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:115a]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1770:ff00  
Bus 001 Device 002: ID 1908:0226 GEMBIRD 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rt73usb                32768  0 
rt2x00usb              24576  1 rt73usb
rt2x00lib              57344  2 rt73usb,rt2x00usb
mac80211              708608  2 rt2x00lib,rt2x00usb
crc_itu_t              16384  1 rt73usb
msi_wmi                16384  0 
sparse_keymap          16384  1 msi_wmi
iwlwifi               188416  0 
cfg80211              524288  3 iwlwifi,mac80211,rt2x00lib
mxm_wmi                16384  0 
wmi                    20480  2 msi_wmi,mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

##### iwconfig ##########################

eth1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root      3482     1  0 17:30 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto HomeNet]] (600 root)
[connection] id=Auto HomeNet | type=802-11-wireless
[802-11-wireless] ssid=HomeNet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto  Samsung Galaxy® S6 Edge]] (600 root)
[connection] id=Auto  Samsung Galaxy® S6 Edge | type=802-11-wireless
[802-11-wireless] ssid=32;83;97;109;115;117;110;103;32;71;97;108;97;120;121;194;174;32;83;54;32;69;100;103;101; | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Auto HomeNet-bdb35064-5be2-49ca-9dfa-54dcb3b51264]] (600 root)
[connection] id=Auto HomeNet | type=802-11-wireless
[802-11-wireless] ssid=HomeNet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rt73usb]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BCF882E0CB338C7C3C172CF
depends:        rt2x00lib,rt2x00usb,crc-itu-t
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512

[rt2x00lib]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     19A5C735A79087003D53D6A
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        0C:8B:EF:E0:C1:E2:89:E4:D8:99:09:26:11:7A:DA:3B:DF:EB:41:9C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt73usb]
nohwcrypt: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (rt73usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   38.747444] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  103.019290] ieee80211 phy0: rt2x00_set_chip: Info - Chipset detected - rt: 2573, rf: 0002, rev: 000a
[  103.039679] rt73usb 1-8:1.0 wlan1: renamed from wlan0
[  103.061751] systemd-udevd[4650]: renamed network interface wlan0 to wlan1
[  127.761590] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'
[  127.764283] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7
[  127.820094] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  129.169927] wlan1: authenticate with <MAC address>
[  129.189409] wlan1: send auth to <MAC address> (try 1/3)
[  129.190956] wlan1: authenticated
[  129.193305] wlan1: associate with <MAC address> (try 1/3)
[  129.196109] wlan1: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=11)
[  129.202230] wlan1: associated
[  129.202238] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  161.240391] wlan1: deauthenticating from <MAC address> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-12-20
Use the Linux Mint Update Manager, click View then select Linux kernels.  Click on 4.2.0-22 and install it

Then ```
wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-15.227938.0.tgz
tar zxvf iwlwifi-7265-ucode-15.227938.0.tgz
cd iwlwifi-7265-ucode-15.227938.0
sudo cp iwlwifi*.ucode /lib/firmware/iwlwifi-7265-15.ucode
```

Reboot

---

### Post by howefield on 2015-12-20
Thread moved to the "*MINT*" forum.

---

### Post by allen17 on 2015-12-20
Jeremy31,

i have successfully updated the kernel but when i try to execute the commands i get the following:

```

mint@mint ~ $ wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-15.227938.0.tgz
--2015-12-20 22:14:13--  https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-15.227938.0.tgz
Resolving wireless.wiki.kernel.org (wireless.wiki.kernel.org)... 198.145.29.82
Connecting to wireless.wiki.kernel.org (wireless.wiki.kernel.org)|198.145.29.82|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1099211 (1.0M) [application/octet-stream]
Saving to: ‘iwlwifi-7265-ucode-15.227938.0.tgz.1’

 0% [                                       ] 0           --.-K/s   in 0s      


Cannot write to ‘iwlwifi-7265-ucode-15.227938.0.tgz.1’ (Success).
mint@mint ~ $ tar zxvf iwlwifi-7265-ucode-15.227938.0.tgz

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now
mint@mint ~ $ cd iwlwifi-7265-ucode-15.227938.0
bash: cd: iwlwifi-7265-ucode-15.227938.0: No such file or directory
mint@mint ~ $ sudo cp iwlwifi*.ucode /lib/firmware/iwlwifi-7265-15.ucode
cp: cannot stat ‘iwlwifi*.ucode’: No such file or directory
mint@mint ~ $ 


```

am i doing something wrong? thanks for the help, i really appreciate it.

---

### Post by jeremy31 on 2015-12-21
You could go into the Downloads folder, right click on the iwlwifi-7265-ucode-15.227938.0 and select extract here, double click on the folder created and hopefully it contains a file named iwlwifi-7265-15.ucode.  When you find the iwlwifi-7265-15.ucode file, right click inside the folder and select "Open in terminal" then enter ```
sudo cp iwlwifi-7265-15.ucode /lib/firmware/
```

Reboot

If it doesn't work, run the wireless script again and post the new results

---

### Post by allen17 on 2015-12-22
Jeremy31,

Ok, so that somewhat worked for me but after i reboot it is now stuck at the splash screen. the linux mint logo sits on the screen for longer than a reasonable amount of time (i actually let it sit for roughly 30 minutes before powering off). I'm actively looking for a solution to this issue but if you have any suggestions that would be great! thanks in advance, hopefully once i get over this hurdle my wifi will be up and running!

---

### Post by jeremy31 on 2015-12-22
When booting press the ESC key when the Linux Mint logo shows up, there could be error messages.  It may want to load an older version of the firmware

---

### Post by allen17 on 2015-12-22
I tried booting and pressing ESC and nothing happened. i tried adding ```
nomodeset xforcevesa
``` as mentioned here: [http://forums.linuxmint.com/viewtopic.php?f=46&t=122257](http://forums.linuxmint.com/viewtopic.php?f=46&t=122257)

the outcome:

1. it stated the following:
   
   Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X
   server output to diagnose the problem?   <Yes>   <No> 

2. after selecting YES:
[HTML]
   X.org X Server 1.17.1
   Release Date: 2015-02-10
   X Protocol Version 11, Revision 0
   Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
   Current Operating System: Linux Mint 4.2.0-11-generic #27~14.01.1-Ubuntu
   Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/pressed/linu
   xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (for technical support please se
   Current version of pixman: 0.30.2
      Before reporting problems, check http://wiki.x.org
      to make sure that you have the latest version/
   Markers: (--)probed, (**) from config file, (==) default setting,
      (++) from command line, (!!)  notice, (II) informational,
   (==)log file: "/var/log/Xorg.0.log", Time: Tue Dec 22 18:14:35 2015
   (==)Using system config file: "/etc/X11/xorg.conf"
   (==)Using system config directory "/usr/share/X11/xorg.conf.d"
   (EE) 
   Fatal server error:
   (EE) no screens found (EE)
   (EE)
   Please consult the X.org foundation support at http://wiki.x.org for help
   (EE) Please also check the log fine at "var/log/Xorg.0.log" for additio
   (EE)
   (EE) Server terminated with error (1). Closing log file.
[/HTML]

3. after exiting that screen i am taken to the command line which gives the following errors:
[HTML]
   [   42.043402] pcieport 000:00:1c.0:   device [8086:a110] error status/mask=00000001/00002000
   [   42.043434] pcieport 000:00:1c.0:   [0] receiver error
   [   42.043459] pcieport 000:00:1c.0:  PCIe Bus error: severity=corrected, type=physical layer, id=00
   [ 162.355092] pcieport 000:00:1c.0:    device [8086:a110] error status/mask=00000001/00002000
   [ 162.355180] pcieport 000:00:1c.0:    [0] receiver error
   [ 162.355249] pcieport 000:00:1c.0:   PCIe Bus error: severity=corrected, type=physical layer, id=00
   [ 176.799288] pcieport 000:00:1c.0:    device [8086:a110] error status/mask=00000001/00002000
   [ 176.799360] pcieport 000:00:1c.0:    [0] receiver error
   [ 176.799417] pcieport 000:00:1c.0:   PCIe Bus error: severity=corrected, type=physical layer, id=00
[/HTML]

after those error messages i am able to enter commands like normal but no GUI. 


as a noob, I'm not sure if this is supposed to give me any important information. I went on wiki.X.org and looked around but didnt find anything that was helpful. 

Any ideas?

---

### Post by jeremy31 on 2015-12-22
Hold the Shift key during boot to get to the Grub menu, select Previous Linux versions or Advanced Options, then select the 3.19 kernel and see if it boots

---

### Post by allen17 on 2015-12-22
Jeremy31,

Thanks for being so patient. Unfortunately there is no Wifi. Here are the results:

```


########## wireless info START ##########

Report from: 23 Dec 2015 02:21 UTC +0000

Booted last: 23 Dec 2015 02:12 UTC +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa

##### kernel ############################

Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: file=/cdrom/preseed/linuxmint.seed, cdrom-detect/try-usb=true, persistent, noprompt, floppy.allowed_drive_mask=0, ignore_uuid, boot=casper, iso-scan/filename=, quiet, splash, --

##### desktop ###########################

Cinnamon

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Device [8086:3165] (rev 81)
    Subsystem: Intel Corporation Device [8086:4010]

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:115a]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 003: ID 1770:ff00  
Bus 001 Device 002: ID 1908:0226 GEMBIRD 
Bus 001 Device 009: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlwifi               188416  0 
cfg80211              524288  1 iwlwifi
msi_wmi                16384  0 
mxm_wmi                16384  0 
sparse_keymap          16384  1 msi_wmi
wmi                    20480  2 msi_wmi,mxm_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.169  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:848887 (848.8 KB)  TX bytes:219500 (219.5 KB)

##### iwconfig ##########################

eth1      no wireless extensions.

usb0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      3584     1  0 02:12 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.169
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Auto Hawthorn - 7]] (600 root)
[connection] id=Auto Hawthorn - 7 | type=802-11-wireless
[802-11-wireless] ssid=Hawthorn - 7 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Auto HomeNet]] (600 root)
[connection] id=Auto HomeNet | type=802-11-wireless
[802-11-wireless] ssid=HomeNet | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Etc/UTC (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth1      no frequency information.

usb0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth1      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlwifi]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     B470AF663F8CCFC606AA966
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x8086:0x3165 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   35.314368] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3165-12.ucode failed with error -2
[   35.314408] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3165-11.ucode failed with error -2
[   35.314435] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3165-10.ucode failed with error -2
[   35.314437] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-3165-10.ucode' failed.
[   35.314462] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-3165-9.ucode failed with error -2
[   35.314463] iwlwifi 0000:02:00.0: request for firmware file 'iwlwifi-3165-9.ucode' failed.
[   35.314465] iwlwifi 0000:02:00.0: no suitable firmware found!
[   35.314649] iwlwifi 0000:02:00.0: Unsupported splx structure
[   38.918247] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  312.087456] rndis_host 1-3:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-3, RNDIS device, <MAC 'usb0' [IF]>

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-12-23
I would keep using 3.19 and go into update manager to uninstal the 4.2 kernel
Then ```
sudo mv /lib/firmware/iwlwifi-7265-10.ucode /lib/firmware/iwlwifi-3165-10.ucode
```

And if things go normally, a reboot will result in using the 3.19 kernel with working wireless

---

### Post by allen17 on 2015-12-28
It still didnt work. is this the only route for an MSi branded laptop? i contacted MSi about this issue and they told me that they only support the OEM installed OS and could not provide me with any help.

---

### Post by jeremy31 on 2015-12-28
> **allen17 said:**
> It still didnt work. is this the only route for an MSi branded laptop? i contacted MSi about this issue and they told me that they only support the OEM installed OS and could not provide me with any help.

It is a newer wifi card and that is the issue.  Post the result of ```
ls /lib/firmware | grep iwlwifi; dmesg | grep iwlwifi
```

It is supported but since the source code is a bit of a mess

---

### Post by jeremy31 on 2015-12-31
Had to search the linux-wireless mailing list and found that this should work
```
wget https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.17.12.0.tgz
tar zxvf iwlwifi-7265-ucode-25.17.12.0.tgz
cd iwlwifi-7265-ucode-25.17.12.0
sudo cp iwlwifi-7265D-12.ucode /lib/firmware/iwlwifi-3165-12.ucode
```
Reboot

Confirmed to work [http://forums.linuxmint.com/viewtopic.php?f=53&t=212884#p1110665](http://forums.linuxmint.com/viewtopic.php?f=53&t=212884#p1110665)

---

### Post by allen17 on 2016-01-08
THANK YOU SO MUCH!!!!!!!!!!! it worked instantly. Sorry it took so long  to try; i lost hope and went out to purchase a sub-par mini wireless N  dongle. Now we're in business with AC !!

---

