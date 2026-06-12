---
title: "iwconfig unknown error 524 after upgrade to dapper"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by mistamcgoo on 2006-06-04
hi, i am experiencing problems with my wifi after having upgraded to dapper

my wifi card is a us robotics 54 mbps usb stick, installed via ndiswrapper. 
the pc is a home built desktop (abit mobo, athlon 1800+, 512 ddr,radon 7000)
In breezy, after booting up i gave the commands 
sudo iwconfig wlan0 essid "myname" key xxxxxxxxxx
sudo dhclient wlan0
and i got connection. (after the dhcp handshake)

now i upgraded with this wifi card, but after the reboot, it no longer works. 
apparently it has been renamed to "eth1" now (onboard nic being eth0 i guess")

i tried reinstalling it with ndiswrapper, seems to work ok but when i give the iwconfig command (now with eth1 instead of wlan0) it returns 
SET failed on device eth1 : unknown error 524

when i just type iwconfig eth1 it gives me the normal lines with
mode, channel, ... at access point it says "invalid". 

anyone any idea if i can fix this? would it help if i just downloaded the iso and give it a fresh install instead of updating?

---

### Post by ranf on 2006-06-06
What's the output of:
```
sudo lshw -C network
```

---

### Post by mistamcgoo on 2006-06-06
this is the output
stijn@stijn-desktop:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:50:8d:46:5c:66
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                          00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverve                          rsion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:e400-e4ff iomemory:ec101000-ec1010ff irq:185
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:3d:b4:00:00:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b
stijn@stijn-desktop:~$    

from what i've been trying out and reading it seems i need to be able to rename the eth1 name to wlan0. ndiswrapper still works properly, but the iwconfig commands simply cant find a wlan0, and gives an error with eth1, i guess because ndiswrapper can't work with the eth1 device name. 

is there any way i can correct this naming problem? i already tried editing the 
/etc/network/interfaces, but that doesnt help. is there any way i can change the eth1 logical name in the output above to wlan0? so it works with ndiswrapper? 
ndiswrapper automatically adds the alias wlan0 when i typed ndiswrapper -m.

 edit : i found out how to change the alias in ndiswrapper to eth1, but it doesnt make any changes, i keep getting he same error messages

---

### Post by ranf on 2006-06-07
I have the suspicion that with the update to Dapper there also came a native Linux driver for your card.

I was hoping to see it listed by lshw.

Can you post the output of this please:
```
lsmod
```

---

### Post by mistamcgoo on 2006-06-07
here is the output of lsmod
Module                  Size  Used by
radeon                116000  1
drm                    73236  2 radeon
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
sg                     37920  0
sd_mod                 19984  0
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
af_packet              22920  2
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
i2c_viapro              8980  0
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
i2c_core               21904  2 i2c_acpi_ec,i2c_viapro
via_ircc               26900  0
irda                  186940  1 via_ircc
snd_via82xx            28824  1
gameport               15496  1 snd_via82xx
usbhid                 38368  0
floppy                 62148  0
snd_ac97_codec         92704  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
crc_ccitt               2304  1 irda
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
tsdev                   8000  0
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
pcspkr                  2180  0
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,s
nd_rawmidi
rtc                    13492  0
usb_storage            74176  0
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,
snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_
device
scsi_mod              139496  3 sg,sd_mod,usb_storage
soundcore              10208  1 snd
psmouse                36228  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
serio_raw               7300  0
via_rhine              23940  0
mii                     5888  1 via_rhine
via_agp                 9856  1
agpgart                34888  2 drm,via_agp
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               32008  0
uhci_hcd               33680  0
usbcore               129668  5 usbhid,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

it seems the problem is indeed caused by something else than the renaming. 
i have renamed eth1 to wlan0 in /etc/iftab, so that the system uses the ndiswrapper alias, but this doesn't help either, i keep on getting the same error 

SET failed on device wlan0 : unknown error 524

the same happens when i rename the ndiswrapper alias to eth1 
SET failed on device eth1 : unknown error 524

---

### Post by ranf on 2006-06-07
I don't see any other wireless driver here. But I also miss ndiswrapper. Isn't that a kernel module?

Have a look at this Wiki page please (section 2.2.3)
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

---

### Post by mistamcgoo on 2006-06-07
i have done a fresh install (to be sure any changes i did by messing around are undone). first i did those lsmod and lshw commands right after install, before i installed ndiswrapper tools. the output is in the attached file before ndis.txt. 
(i am afraid this thread will become very long otherwise)

next i installed ndiswrapper and set it up according to the link you provided.
and did those commands again, the output is in the file after ndis.txt 
the outcome is still the same though, i still get the same error.
sudo iwconfig eth1 essid default key 0000000000
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Unknown error 524. 

strangely enough, when i did the ifup eth1 command,  in the output 
i saw this 
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down

does this mean it discovers the dhcp of my AP? i have copy pasted the complete output of the command in after ndis.txt, below the other commands. 

from what i think to understand, is it possible dapper tries to use something called
islsm_device as a native driver for my card?

---

### Post by ranf on 2006-06-08
You are right. `islsm' is a Prism54 WLAN driver.
Look it up yourself:
```
modinfo islsm
```

You have 2 options now:

1 remove ndiswrapper and try islsm
2 put islsm into the blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
and use ndiswrapper

---

### Post by mistamcgoo on 2006-06-08
Can you tell me how exaclty i blacklist islsm? i added the lines
# islsm
blacklist islsm 

to the blacklist, but this doesn't seem to make any difference, i still get the error
message. 
i also renamed eth1 to wlan0 in /etc/iftab to make the alias wlan0, but again, this doesn't help.

---

### Post by ranf on 2006-06-09
From your lsmod output:
```
islsm_usb              32260  0
islsm_device           12040  1 islsm_usb
islsm                  37644  2 islsm_usb,islsm_device
ieee80211softmac       29696  1 islsm
ieee80211              37064  2 islsm,ieee80211softmac
ieee80211_crypt         6272  1 ieee80211

```

I think you need these 3:
```

blacklist islsm
blacklist islsm_usb
blacklist islsm_device

```
I'm not sure about the ones starting with ieee.

Ah, and you should reboot after changing the blacklist.

---

### Post by mistamcgoo on 2006-06-09
It looks like that did the trick =D> . i am online with dapper since a minute ago :-D 
thank you very much for all the help. I wouldn't have found that out by my self. 

i added all  the lines to the blacklist (also the ones with ieee), 
and started the ndiswrapper configuration again from depmod -a . 

strangely enough, the card is called wlan0, in /etc/iftab
there's only eth0 and eth1 (which i don't have, only 1 onboard
ethernet port on this pc). but this seems to be no real problem.
I hope it keeps on working after i rebooted :)

again, a very big thank you for all the help.

---

