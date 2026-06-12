---
title: "voyo v2 wifi+BT driver"
date: 2016-10-18
forum: MINT
---

### Post by gaut2 on 2016-10-18
Hello,

[COLOR=#000000]I've installed ubuntu 16.10 on my Voyo v2. It's a windows 10 TV box which i would like to use as a portable computer, i don t know what is the wifi chip on this hardware... Apparently it is not supported by ubuntu : i got this dmesg error message : 
[/COLOR][COLOR=#000000]> [/COLOR][COLOR=#000000]
[45.969880] gpio-keys gpio-keys.0.auto: unable to claim irq 8; error -16
[45.969910] gpio-keys: probe of gpio-keys.0.auto failed with error -16
[46.300624] brcmfmac mmc0:0001:1: Direct firmware load for brcm/brcmfmac43430-sdio.bin failed with error -2. 
[/COLOR][COLOR=#000000][/COLOR][COLOR=#000000]
so no wifi and bluetooth right now.[/COLOR]
[COLOR=#000000]The problem is, while I've been using ubuntu for a couple years, I don't know anything about how to get a working wifi+BT driver to get the wifi+BT working. [/COLOR][COLOR=#000000]More to the point, I don't know enough to really be sure of what questions to ask, which really makes it harder to just google the information and research it. 

[/COLOR][COLOR=#000000]Anyone help me with what I should be looking up?[/COLOR]

---

### Post by jeremy31 on 2016-10-18
Just do ```
cd /lib/firmware/brcm
```
```
sudo wget http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/brcm/brcmfmac43430-sdio.bin
```

Reboot and I suspect wireless will work.  If it doesn't post results for ```
dmesg | grep brcmfmac
``` as it may also look for a txt file

For the bluetooth post results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by gaut2 on 2016-10-18
thanks for your help. The wifi is still not working,

now the message i got for : dmesg | grep brcmfmac
is : 
> [    7.456209] usbcore: registered new interface driver brcmfmac
[    7.500368] brcmfmac_sdio mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430-sdio.txt failed with error -2
and for : lsusb; dmesg | egrep -i 'blue|firm'
is :
> Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0b95:772b ASIX Electronics Corp. AX88772B
Bus 001 Device 007: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 003: ID 05e3:0718 Genesys Logic, Inc. IDE/SATA Adapter
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.215072] [Firmware Info]: PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] not reserved in ACPI motherboard resources
[    1.887459] [Firmware Bug]: No valid trip found
[    7.077217] [Firmware Bug]: No valid trip found
[    7.500368] brcmfmac_sdio mmc1:0001:1: Direct firmware load for brcm/brcmfmac43430-sdio.txt failed with error -2

---

### Post by jeremy31 on 2016-10-18
I may not be able to help with the bluetooth but there is a chance with the wifi.  Post results for ```
cat /sys/firmware/efi/efivars | grep nvram
```

---

### Post by gaut2 on 2016-10-18
ok, here's the result of the command :
cat /sys/firmware/efi/efivars | grep nvram
> cat: /sys/firmware/efi/efivars: is a directory

---

### Post by jeremy31 on 2016-10-18
Sorry it should have been ```
ls /sys/firmware/efi/efivars | grep nvram
```
At least I know the directory exists now and there is hope for wifi

---

### Post by gaut2 on 2016-10-18
[COLOR=#000000]ok, the result of the command :[/COLOR]
ls /sys/firmware/efi/efivars | grep nvram

is nothing.....

---

### Post by jeremy31 on 2016-10-19
Lets see if the file I found will work
```
cd /lib/firmware/brcm
sudo wget https://raw.githubusercontent.com/RPi-Distro/firmware-nonfree/master/brcm80211/brcm/brcmfmac43430-sdio.txt
```

Reboot

---

### Post by gaut2 on 2016-10-19
ok, now the command dmesg | grep brcmfmac give me this :

> [    7.536457] usbcore: registered new interface driver brcmfmac

and the command iwconfig this :
> lo        no wireless extensions.


enx00e04c4015b7  no wireless extensions.

---

### Post by jeremy31 on 2016-10-19
Can you run the wireless script, link is in my signature and post results

---

### Post by gaut2 on 2016-10-21
ok, i ran those commands :

sudo apt-get update
sudo apt-get dist-upgrade

and then the wireless script which give this text file :
```


########## wireless info START ##########


Report from: 21 Oct 2016 15:36 CEST +0200


Booted last: 21 Oct 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 18 Sarah
Release:	18
Codename:	sarah


##### kernel ############################


Linux 4.8.1-040801-generic #201610071031 SMP Fri Oct 7 14:34:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0b95:772b ASIX Electronics Corp. AX88772B
Bus 001 Device 008: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 004: ID 05e3:0718 Genesys Logic, Inc. IDE/SATA Adapter
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 05e3:0751 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


snd_soc_sst_bytcr_rt5640    20480  0
brcmfmac              249856  0
snd_soc_rt5645        147456  0
brcmutil               16384  1 brcmfmac
cfg80211              589824  1 brcmfmac
snd_soc_rt5640        118784  2 snd_soc_sst_bytcr_rt5640
snd_soc_sst_match      16384  2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_rl6231         16384  2 snd_soc_rt5640,snd_soc_rt5645
snd_soc_core          233472  4 snd_soc_sst_bytcr_rt5640,snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform
snd_pcm               110592  6 snd_soc_sst_bytcr_rt5640,snd_pcm_dmaengine,snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform,snd_soc_core
rfkill                 24576  3 rfkill_gpio,cfg80211
wmi                    16384  0
mmc_core              147456  4 sdhci,mmc_block,sdhci_acpi,brcmfmac


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e8da:ffd8:c9e1:85be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37144 (37.1 KB)  TX bytes:19011 (19.0 KB)


##### iwconfig ##########################


lo        no wireless extensions.


enx<IF from MAC [IF1]>  no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF1]>


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       691     1  0 15:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88772C
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772B USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Connexion filaire 1
GENERAL.CON-UUID:                       3e97552b-3ad8-31d8-8434-488c01ced0cb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3e97552b-3ad8-31d8-8434-488c01ced0cb | Connexion filaire 1
IP4.ADDRESS[1]:                         192.168.1.35/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = entreprise
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1477143324
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.35
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::e8da:ffd8:c9e1:85be/64
IP6.GATEWAY:                            


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enx<IF from MAC [IF1]>  no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


##### module infos ######################


[brcmfmac]
filename:       /lib/modules/4.8.1-040801-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365c-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
depends:        mmc_core,brcmutil,cfg80211
intree:         Y
vermagic:       4.8.1-040801-generic SMP mod_unload modversions 
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:Do not use internal roaming engine (int)


[brcmutil]
filename:       /lib/modules/4.8.1-040801-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
depends:        
intree:         Y
vermagic:       4.8.1-040801-generic SMP mod_unload modversions 


[cfg80211]
filename:       /lib/modules/4.8.1-040801-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       4.8.1-040801-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v02D0p4324d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0p4330d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0p4354d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0p4356d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA94Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA94Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA9A6d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA9A6d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############]
```

---

### Post by jeremy31 on 2016-10-21
*Thread moved to **MINT**.*

If that file isn't making it work, lets change it ```
sudo -H gedit /lib/firmware/brcm/brcmfmac43430-sdio.txt
```

And paste the following in, replacing the original
```
manfid=0x2d0
prodid=0x0653
vendid=0x14e4
devid=0x4386
boardtype=0x0653
boardrev=0x1203
boardnum=22
macaddr=02:0A:F7:2A:3B:4C
sromrev=3
boardflags=0x0090201
xtalfreq=37400
nocrc=1
ag0=255
aa2g=1
aa5g=1
ccode=ALL
pa0itssit=0x20
pa0b0=6747
pa0b1=-808
pa0b2=-178
tssifloor2g=69
rssismf2g=0xf
rssismc2g=0x8
rssisav2g=0x1
cckPwrOffset=3
rssismf5g=0xf
rssismc5g=0x7
rssisav5g=0x3
pa1lob0=5659
pa1lob1=-693
pa1lob2=-178
tssifloor5gl=93
pa1b0=5172
pa1b1=-671
pa1b2=-212
tssifloor5gm=77
pa1hib0=5320
pa1hib1=-663
pa1hib2=-179
tssifloor5gh=74
rxpo5g=0
maxp2ga0=0x4E
cck2gpo=0x0000
ofdm2gpo=0x42000000
mcs2gpo0=0x2222
mcs2gpo1=0x7662
maxp5ga0=0x46
maxp5gla0=0x46
maxp5gha0=0x46
ofdm5gpo=0x52222222
ofdm5glpo=0x52222222
ofdm5ghpo=0x52222222
mcs5gpo0=0x0000
mcs5gpo1=0x8550
mcs5glpo0=0x0000
mcs5glpo1=0x8550
mcs5ghpo0=0x0000
mcs5ghpo1=0x8550
swctrlmap_2g=0x00080008,0x00100010,0x00080008,0x011010,0x11f
swctrlmap_5g=0x00020002,0x00040004,0x00020002,0x011010,0x2fe
gain=32
triso2g=8
triso5g=8
loflag=0
iqlocalidx5g=40
dlocalidx5g=70
iqcalidx5g=50
lpbckmode5g=1
txiqlopapu5g=0
txiqlopapu2g=0
dlorange_lowlimit=5
txalpfbyp=1
txalpfpu=1
dacrate2xen=1
papden2g=1
papden5g=1
gain_settle_dly_2g=4
gain_settle_dly_5g=4
noise_cal_po_2g=-1
noise_cal_po_40_2g=-1
noise_cal_high_gain_2g=73
noise_cal_nf_substract_val_2g=346
noise_cal_po_5g=-1
noise_cal_po_40_5g=-1
noise_cal_high_gain_5g=73
noise_cal_nf_substract_val_5g=346
cckpapden=0
paparambwver=1

```
Save, exit gedit and reboot

---

### Post by gaut2 on 2016-10-22
Ok, i just did it and still no wifi, the result of dmesg | grep brcmfmac :
> [   10.344846] usbcore: registered new interface driver brcmfmac
[   11.404717] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[   12.432854] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50
[   13.437859] brcmfmac: brcmf_sdio_htclk: HT Avail timeout (1000000): clkctl 0x50


here is the result of the new wireless script file :
```


########## wireless info START ##########


Report from: 22 Oct 2016 15:10 CEST +0200


Booted last: 22 Oct 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	LinuxMint
Description:	Linux Mint 18 Sarah
Release:	18
Codename:	sarah


##### kernel ############################


Linux 4.8.1-040801-generic #201610071031 SMP Fri Oct 7 14:34:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0b95:772b ASIX Electronics Corp. AX88772B
Bus 001 Device 009: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 003: ID 05e3:0718 Genesys Logic, Inc. IDE/SATA Adapter
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


snd_soc_sst_bytcr_rt5640    20480  0
snd_soc_rt5645        147456  0
brcmfmac              249856  0
brcmutil               16384  1 brcmfmac
cfg80211              589824  1 brcmfmac
snd_soc_rt5640        118784  2 snd_soc_sst_bytcr_rt5640
snd_soc_rl6231         16384  2 snd_soc_rt5640,snd_soc_rt5645
snd_soc_sst_match      16384  2 snd_soc_sst_bytcr_rt5640,snd_intel_sst_acpi
snd_soc_core          233472  4 snd_soc_sst_bytcr_rt5640,snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform
snd_pcm               110592  6 snd_soc_sst_bytcr_rt5640,snd_pcm_dmaengine,snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform,snd_soc_core
rfkill                 24576  3 rfkill_gpio,cfg80211
wmi                    16384  0
mmc_core              147456  4 sdhci,mmc_block,sdhci_acpi,brcmfmac


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enx<IF from MAC [IF1]> Link encap:Ethernet  HWaddr <MAC 'enx<IF from MAC [IF1]>' [IF1]>  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e8da:ffd8:c9e1:85be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15306 (15.3 KB)  TX bytes:17398 (17.3 KB)


##### iwconfig ##########################


enx<IF from MAC [IF1]>  no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enx<IF from MAC [IF1]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx<IF from MAC [IF1]>
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enx<IF from MAC [IF1]>


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       762     1  0 15:07 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         ASIX Elec. Corp.
GENERAL.PRODUCT:                        AX88772C
GENERAL.DRIVER:                         asix
GENERAL.DRIVER-VERSION:                 22-Dec-2011
GENERAL.FIRMWARE-VERSION:               ASIX AX88772B USB 2.0 Ethernet
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Connexion filaire 1
GENERAL.CON-UUID:                       3e97552b-3ad8-31d8-8434-488c01ced0cb
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3e97552b-3ad8-31d8-8434-488c01ced0cb | Connexion filaire 1
IP4.ADDRESS[1]:                         192.168.1.35/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = entreprise
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1477228083
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.35
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::e8da:ffd8:c9e1:85be/64
IP6.GATEWAY:                            


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enx<IF from MAC [IF1]>  no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[brcmfmac]
filename:       /lib/modules/4.8.1-040801-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11 wireless LAN fullmac driver.
author:         Broadcom Corporation
firmware:       brcm/brcmfmac4356-sdio.bin
firmware:       brcm/brcmfmac4354-sdio.bin
firmware:       brcm/brcmfmac43455-sdio.bin
firmware:       brcm/brcmfmac43430-sdio.bin
firmware:       brcm/brcmfmac4339-sdio.bin
firmware:       brcm/brcmfmac43362-sdio.bin
firmware:       brcm/brcmfmac4335-sdio.bin
firmware:       brcm/brcmfmac43340-sdio.bin
firmware:       brcm/brcmfmac4334-sdio.bin
firmware:       brcm/brcmfmac4330-sdio.bin
firmware:       brcm/brcmfmac4329-sdio.bin
firmware:       brcm/brcmfmac43241b5-sdio.bin
firmware:       brcm/brcmfmac43241b4-sdio.bin
firmware:       brcm/brcmfmac43241b0-sdio.bin
firmware:       brcm/brcmfmac43143-sdio.bin
firmware:       brcm/brcmfmac43569.bin
firmware:       brcm/brcmfmac43242a.bin
firmware:       brcm/brcmfmac43236b.bin
firmware:       brcm/brcmfmac43143.bin
firmware:       brcm/brcmfmac4371-pcie.bin
firmware:       brcm/brcmfmac4366c-pcie.bin
firmware:       brcm/brcmfmac4366b-pcie.bin
firmware:       brcm/brcmfmac4365c-pcie.bin
firmware:       brcm/brcmfmac4365b-pcie.bin
firmware:       brcm/brcmfmac4359-pcie.bin
firmware:       brcm/brcmfmac4358-pcie.bin
firmware:       brcm/brcmfmac43570-pcie.bin
firmware:       brcm/brcmfmac4356-pcie.bin
firmware:       brcm/brcmfmac4350c2-pcie.bin
firmware:       brcm/brcmfmac4350-pcie.bin
firmware:       brcm/brcmfmac43602-pcie.bin
depends:        mmc_core,brcmutil,cfg80211
intree:         Y
vermagic:       4.8.1-040801-generic SMP mod_unload modversions 
parm:           txglomsz:Maximum tx packet chain size [SDIO] (int)
parm:           debug:Level of debug output (int)
parm:           p2pon:Enable legacy p2p management functionality (int)
parm:           feature_disable:Disable features (int)
parm:           alternative_fw_path:Alternative firmware path (string)
parm:           fcmode:Mode of firmware signalled flow control (int)
parm:           roamoff:Do not use internal roaming engine (int)


[brcmutil]
filename:       /lib/modules/4.8.1-040801-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
depends:        
intree:         Y
vermagic:       4.8.1-040801-generic SMP mod_unload modversions 


[cfg80211]
filename:       /lib/modules/4.8.1-040801-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
depends:        rfkill
intree:         Y
vermagic:       4.8.1-040801-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


grep: /sys/module/brcmfmac/parameters/alternative_fw_path: Permission denied
grep: /sys/module/brcmfmac/parameters/debug: Permission denied
grep: /sys/module/brcmfmac/parameters/roamoff: Permission denied
[brcmfmac]


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v02D0p4324d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0p4330d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0p4354d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0p4356d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA94Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA94Dd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA9A6d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v02D0pA9A6d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


########## wireless info END ############
```

---

### Post by jeremy31 on 2016-10-22
I would see if ```
mount -t efivarfs efivarfs /sys/firmware/efi/efivars
```
Then post what ```
ls /sys/firmware/efi/efivars
```
reveals as those are the only brcmfmac43430-sdio.txt files I could find on the internet

---

### Post by gaut2 on 2016-10-22
here's the result for the first command :

> sudo mount -t efivarfs efivarfs /sys/firmware/efi/efivars


mount: efivarfs is already mounted or /sys/firmware/efi/efivars busy
       efivarfs is already mounted on /sys/firmware/efi/efivars

and for the second :
> 

ls /sys/firmware/efi/efivars


AcpiGlobalVariable-c020489e-6db2-4ef2-9aa5-ca06fc11d36a
AuthVarKeyDatabase-aaf32c78-947b-439a-a180-2e144ec37792
Boot0000-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0001-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0002-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0003-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot0004-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot2001-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot2002-8be4df61-93ca-11d2-aa0d-00e098032b8c
Boot2003-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootCurrent-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootOrder-8be4df61-93ca-11d2-aa0d-00e098032b8c
BootType-a04a27f4-df00-4d42-b552-39511302113d
BugCheckCode-ba57e015-65b3-4c3c-b274-659192f699e3
BugCheckParameter1-ba57e015-65b3-4c3c-b274-659192f699e3
BugCheckProgress-ba57e015-65b3-4c3c-b274-659192f699e3
certdb-59d1c24f-50f1-401a-b101-f33e0daed443
ColdQ2SEnableVariable-cccd8c8e-8915-4d12-bb76-0d49b4fc0dcd
ConIn-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConInCandidateDev-59d1c24f-50f1-401a-b101-f33e0daed443
ConInDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOut-8be4df61-93ca-11d2-aa0d-00e098032b8c
ConOutCandidateDev-59d1c24f-50f1-401a-b101-f33e0daed443
ConOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
Custom-a04a27f4-df00-4d42-b552-39511302113d
CustomSecurity-59d1c24f-50f1-401a-b101-f33e0daed443
dbDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
dbx-d719b2cb-3d3a-4596-a3bc-dad00e67656f
dbxDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
ErrOutDev-8be4df61-93ca-11d2-aa0d-00e098032b8c
IrsiInfo-5bce4c83-6a97-444b-63b4-672c014742ff
KEKDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
Lang-8be4df61-93ca-11d2-aa0d-00e098032b8c
LangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
LastBootOSVariable-936d3077-9722-41a8-88ae-91a7b7594a3c
MemoryConfig-10ba6bbe-a97e-41c3-9a07-607ad9bd60e5
MemoryOverwriteRequestControl-e20939be-32d4-41be-a150-897f85d49829
MsdmAddress-fd21bf2b-f5d1-46c5-aee3-c60158339239
MTC-eb704011-1402-11d3-8e77-00a0c969723b
OsIndications-8be4df61-93ca-11d2-aa0d-00e098032b8c
OsIndicationsSupported-8be4df61-93ca-11d2-aa0d-00e098032b8c
PhysicalBootOrder-59d1c24f-50f1-401a-b101-f33e0daed443
PKDefault-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformCpuInfo-10ba6bbe-a97e-41c3-9a07-607ad9bd60e5
PlatformInfo-10ba6bbe-a97e-41c3-9a07-607ad9bd60e5
PlatformLang-8be4df61-93ca-11d2-aa0d-00e098032b8c
PlatformLangCodes-8be4df61-93ca-11d2-aa0d-00e098032b8c
Regparm-49e3577e-71fb-46cc-a4a3-21084b7bd99f
RestoreFactoryDefault-59d1c24f-50f1-401a-b101-f33e0daed443
SecureBoot-8be4df61-93ca-11d2-aa0d-00e098032b8c
SecureBootEnforce-59d1c24f-50f1-401a-b101-f33e0daed443
Setup-a04a27f4-df00-4d42-b552-39511302113d
SetupMode-8be4df61-93ca-11d2-aa0d-00e098032b8c
SignatureSupport-8be4df61-93ca-11d2-aa0d-00e098032b8c
SmmEmmcCardDataVariable-3503b13d-2bd7-43ca-ba63-a1dfaa68da46
Timeout-8be4df61-93ca-11d2-aa0d-00e098032b8c
TrEEPhysicalPresence-f24643c2-c622-494e-8a0d-4632579c2d5b
TrEEPhysicalPresenceFlags-f24643c2-c622-494e-8a0d-4632579c2d5b
VendorKeys-8be4df61-93ca-11d2-aa0d-00e098032b8c

---

### Post by gaut2 on 2016-10-22
i was wondering :

can i use the windows drivers to get my wifi and bluetooth working?

---

### Post by jeremy31 on 2016-10-22
If you are talking about ndiswrapper, it won't work as it only works for wifi and needs Windows XP driver files which might not be available

---

### Post by gaut2 on 2016-10-22
ok,

so i have to wait for a linux driver....

---

### Post by gjrdimaandal on 2017-03-26
Hi gaut2,

May I know were did you get your installer for Voyo Mini PC. Mine is V1 anyways. When I tried to install the iso downloaded directly from Ubuntu website, it just give me black screen with underscore on top left. So I wonder how you manage to install it on your V2 mini pc might as well give me the link on where I can download the iso file. Thank you..

I also sent you a PM...Thanks again;)

---

