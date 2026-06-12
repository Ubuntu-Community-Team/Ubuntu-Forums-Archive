---
title: "[resolved] Problem with HomePNA"
date: 2004-12-26
forum: Installation &amp; Upgrades
---

### Post by Ufo on 2004-12-26
Hi,

I'm new to Linux and to Ubuntu. I´m not even very good in english. So guestions may be stupid and in bad language, sorry about that.
 My problem is I can't get network working in Ubuntu (Warty-release-install-i386.iso).
It works fine with Ubuntu Live CD (Warty-release-live-i386.iso) and with Debian Sarge, installed from Sarge-i386-netinst.iso (all downloaded 12.11.2004).

 I have PCI Home Networking Adapter (HomePNA) and network settings come via DHCP. 
There is also network connection in motherboard, which is not in use.

Installation detected card, but could not get DHCP settings.
After installation, I tried coping /etc/network/interfaces file from Live CD, but that did not help.

After running ifconfig eth1 up, I ran dhclient, but it could not get settings.
In Network tools, there are no ipv4 information, ipv6 information are same as in Live CD.
I have configured it in Network tools to use DHCP and with static information, but in both cases it can't get connection. Activate check mark dissappears after a while.
When I boot into Live CD or Debian, there is light in green led in network card, but when I boot in Ubuntu the led is off. 

Here is output of lsmod:

Module                  Size  Used by
proc_intf               3968  0 
freq_table              4356  0 
cpufreq_userspace       5336  0 
cpufreq_powersave       2048  0 
ipv6                  230020  8 
button                  6936  0 
ac                      5132  0 
battery                 9740  0 
pcnet32                25864  0 
mii                     4864  1 pcnet32
crc32                   4608  1 pcnet32
shpchp                 87276  0 
pciehp                 83948  0 
pci_hotplug            30640  2 shpchp,pciehp
snd_intel8x0           33068  4 
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0 
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
forcedeth              16128  0 
ehci_hcd               27780  0 
ohci_hcd               19460  0 
usbcore               104292  4 ehci_hcd,ohci_hcd
nvidia_agp              7580  1 
agpgart                31784  1 nvidia_agp
analog                 10784  0 
gameport                4736  2 snd_intel8x0,analog
floppy                 54996  0 
pcspkr                  3816  0 
rtc                    12216  0 
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
parport_pc             32064  1 
lp                     10436  0 
parport                37320  2 parport_pc,lp
ide_cd                 38276  0 
tsdev                   7168  0 
evdev                   9088  0 
cdrom                  35872  1 ide_cd
mousedev               10124  1 
psmouse                17800  0 
ext3                  109544  2 
jbd                    54552  1 ext3
ide_generic             1664  0 
ide_disk               16768  4 
amd74xx                13340  1 
ide_core              125272  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   25904  668 
fan                     4236  0 
thermal                13200  0 
processor              17712  1 thermal
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

-----
Here is etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



iface eth1 inet dhcp
name Ethernet lähiverkkokortti

-----
Here is output of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

-------
Here is output of ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:E0:7D:9B:3B:BE  
          inet6 addr: fe80::2e0:7dff:fe9b:3bbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:18 dropped:0 overruns:0 carrier:18
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:4824 (4.7 KiB)
          Interrupt:201 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2067776 (1.9 MiB)  TX bytes:2067776 (1.9 MiB)


Any help and suggestions are welcome  :)

---

### Post by Ufo on 2004-12-27
Hi

 I managed to solve the problem after some googling.
I had to add following line to /etc/modules

pcnet32 homepna=1

So this is posted from Ubuntu!  :D

---

