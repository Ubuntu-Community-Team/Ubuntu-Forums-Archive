---
title: "Switching from eth0 to eth1"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by jlerossignol on 2013-02-11
eth0 died on my dual boot system at home. So I get a D-Link DGE-528T to  replace it. Ubuntu 11.10 appears to detect (ie it's listed as eth1), but  it won't work.

So I tried to install the files supplied with the card. which are design  for 2.4/2.6 Linux Headers, not the 3.0 which I have. No joy... they  won't install because of wrong headers.

The Windows side finds it just fine, but as stated ubuntu won't. How do I fix this?

**ifconfig -a** yields;

[FONT=Courier New]eth1      Link encap:Ethernet  HWaddr 00:24:8c:4e:34:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

eth2      Link encap:Ethernet  HWaddr 1c:7e:e5:2a:c9:58  
          inet6 addr: fe80::1e7e:e5ff:fe2a:c958/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4419 (4.4 KB)
          Interrupt:17 Base address:0x4c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44824 (44.8 KB)  TX bytes:44824 (44.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:b0:70:83:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][COLOR=Silver][FONT=Courier New]
[/FONT]

[/COLOR]and **dmesg | grep eth** responded with

[FONT=Courier New][    2.229915] r8169 0000:05:01.0: eth0: RTL8169sb/8110sb at 0xf8014c00, 1c:7e:e5:2a:c9:58, XID 10000000 IRQ 17
[   10.244444] udevd[405]: renamed network interface eth0 to eth2
[   21.555988] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.960201] r8169 0000:05:01.0: eth2: link down
[   21.960343] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   23.595442] r8169 0000:05:01.0: eth2: link up
[   23.595616] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   33.624011] eth2: no IPv6 routers present[/FONT]

---

### Post by fdrake on 2013-02-11
i do believe you may need to build your own kernel....

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

google will offer a lot of links.

my suggestion: find an ubuntu with an old kernel and install it .
I don't dare to compile my own kernel myself due to time requirements..

if the company has created some new installation files suppertin kernel 3.0 then good for you, but it does not look like it's the case..

---

### Post by schragge on 2013-02-11
Don't know if it'll help, but try to
```
EXCLUDE_INTERFACES=eth0
```in */etc/default/networking*

And look at what you've got in */etc/network/interfaces*

---

### Post by MAFoElffen on 2013-02-11
> **schragge said:**
> Don't know if it'll help, but try to
```
EXCLUDE_INTERFACES=eth0
```in */etc/default/networking*

[COLOR="Red"]And look at what you've got in */etc/network/interfaces*[/COLOR]

Please post /etc/networking/interfaces

I think what we'll find is that the original install probes your hardware... on NIC's, it creates the interfaces file with the NIC hardware it finds (physically connected ports) and sets the defs for whatever is chosen as the primary connected ports (automatically connect to default). For anything it doesn't specifically define in there it just assumes defaults or inserts dynamic values... If set in that file, it uses those values.

If you define/hardcode values for a port that is not physically connected or not there, bad juju... it will probe that port and hang... or at least be probing for 2-5 minutes if it does recover, so first do this to make sure linux see's it:
```

lspci -vnn | grep eth1

```
So in that file (/etc/networking/interfaces), it will probably have generic def's set for eth0 for dhcp... If you edit that file and change all from eth0 to eth1... that should do you.  

You shouldn't need to compile a driver for your card unless the version of Linux you're running does not specifically support the card you bought. (proprietary/not opensource) That could still be true, but set it up for success first, then you can see if is supported or not.

EDIT-- If you do end up having to compile a proprietary driver, the header error is probing uname -r to ensure it has a 2.6.x kernel and doesn't recognize or know that 3.x.x kernels are a 2.6.x kernel with a naming convention change... so the header would need editing to include the 3.x.x kernels. But if I happen upon a "not opensource/proprietary" NIC in my installs, I always check to see if package linux-firmware-nonfree would cover it first...

---

### Post by jlerossignol on 2013-02-15
> **schragge said:**
> Don't know if it'll help, but try to
```
EXCLUDE_INTERFACES=eth0
```in */etc/default/networking*

And look at what you've got in */etc/network/interfaces*

I'm worried now, because there is no /etc/default/networking/


The 
lspci -vnn | grep eth1resulted in nothing. So I expanded it and here are the two ethernet controllers along with the wireless network. The D-Link is the one I want to work

02:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8226]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe9c0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at cc00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ATL1E
    Kernel modules: atl1e

05:00.0 Network controller [0280]: Ralink corp. RT2561/RT61 rev B 802.11g [1814:0302]
    Subsystem: D-Link System Inc DWA-510 Wireless G Desktop Adapter [1186:3a71]
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at febf8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci

05:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
    Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300]
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    I/O ports at e800 [size=256]
    Memory at febf7c00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by MAFoElffen on 2013-02-16
When you post code, results or commands, please use advanced post, paste the text in, highlight it, then look u to the post tools bar and click on the "#" icon. It will put code tags around the text. It's a lot easier to read... and it displays what is posted it a box without getting translated.
 
I'm not saying this for you to go back and edit your old posts, but for what comes next.

Please post your /etc/network/interfaces file (in a code box.)

Then start your file manager. Go to your folder that contains the header file of the source for your network card driver. Right click on the header file and compress it to a .tar.gz file. Attach it to your post.

Enough info to get you going?

---

### Post by fdrake on 2013-02-16
if you don't have /etc/networking/interfaces
use instead /etc/network/interfaces

---

### Post by schragge on 2013-02-16
> **jlerossignol said:**
> I'm worried now, because there is no /etc/default/networking :oops: Sorry, I was wrong: it's not present on Ubuntu. (I'm using Debian wheezy).

---

### Post by MAFoElffen on 2013-02-16
> **jlerossignol said:**
> eth0 died on my dual boot system at home. So I get a D-Link DGE-528T to  replace it. Ubuntu 11.10 appears to detect (ie it's listed as eth1), but  it won't work.

So I tried to install the files supplied with the card. which are designed  for 2.4/2.6 Linux Headers, not the 3.0 which I have. No joy... they  won't install because of wrong headers.

<<Edited by MAFoElffen>>

and **dmesg | grep eth** responded with

[    2.229915] r8169 0000:05:01.0: eth0: RTL8169sb/8110sb at 0xf8014c00, 1c:7e:e5:2a:c9:58, XID 10000000 IRQ 17
[   10.244444] udevd[405]: renamed network interface eth0 to eth2
[   21.555988] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.960201] r8169 0000:05:01.0: eth2: link down
[   21.960343] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   23.595442] r8169 0000:05:01.0: eth2: link up
[   23.595616] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[   33.624011] eth2: no IPv6 routers present
See the first line of dmesg where it used module r8169.so for eth0? Module r8169.so is the correct kernel module driver for your new card.

Later you posted the results of lspci:
```

05:01.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)
Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300]
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
I/O ports at e800 [size=256]
Memory at febf7c00 (32-bit, non-prefetchable) [size=256]
Expansion ROM at febc0000 [disabled] [size=128K]
Capabilities: <access denied>
Kernel driver in use: r8169
Kernel modules: r8169

```
So your system is seeing it and is using the correct kernel module. I didn't review the linux changelog for that module, but...

There was a problem back with about linux kernel 2.6.10 where this module (r8169.c) needed to be patched to add the new address address for this card's revision B model- 1186.4300 (old version, revision A, of that card had address 10ec:8169), but since it's being seen by lspci, So, by the syslog, it seems as if r8169 is up and is able to address it... So it seems that later module code was patched to also look at that address.

Your dmesg (syslog) said that card came up as eth0, which came up and was ready as "eth2." And eth1 never fully came up (your wireless?). If you could search in the syslog further for:
```

dmesg | grep r8169

```
Then maybe we can see if there where any other mention concerning that module...

So still waiting on the info requested in my last post. Thinking it's just a problem of how it's being addressed.

---

### Post by jlerossignol on 2013-03-17
> **MAFoElffen said:**
> When you post code, results or commands, please use advanced post, paste the text in, highlight it, then look u to the post tools bar and click on the "#" icon. It will put code tags around the text. It's a lot easier to read... and it displays what is posted it a box without getting translated.
 
I'm not saying this for you to go back and edit your old posts, but for what comes next.

Please post your /etc/network/interfaces file (in a code box.)

Then start your file manager. Go to your folder that contains the header file of the source for your network card driver. Right click on the header file and compress it to a .tar.gz file. Attach it to your post.

Enough info to get you going?

I've added "EXCLUDE_INTERFACES=eth0" as fdrake said, so it's now;

```

auto lo
iface lo inet loopback
EXCLUDE_INTERFACES=eth0

```

I don't know where to find the header files for the source for your network card driver. I could use the files I tried to install from, but I don't think they worked.

---

### Post by jlerossignol on 2013-03-17
> **MAFoElffen said:**
> See the first line of dmesg where it used module r8169.so for eth0? Module r8169.so is the correct kernel module driver for your new card.

Your dmesg (syslog) said that card came up as eth0, which came up and was ready as "eth2." And eth1 never fully came up (your wireless?). If you could search in the syslog further for:
```

dmesg | grep r8169

```
Then maybe we can see if there where any other mention concerning that module...

So still waiting on the info requested in my last post. Thinking it's just a problem of how it's being addressed.

```

[    2.238285] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.238304] r8169 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.238326] r8169 0000:05:01.0: (unregistered net_device): no PCI Express capability
[    2.238793] r8169 0000:05:01.0: eth0: RTL8169sb/8110sb at 0xf8014c00, 1c:7e:e5:2a:c9:58, XID 10000000 IRQ 17
[  109.312504] r8169 0000:05:01.0: eth2: link down
[  110.875193] r8169 0000:05:01.0: eth2: link up
[  231.724449] Modules linked in: pci_stub vboxpci(+) vboxnetadp vboxnetflt vboxdrv parport_pc ppdev binfmt_misc dm_crypt nvidia(P) snd_usb_audio snd_usbmidi_lib snd_hda_codec_realtek gspca_stv06xx gspca_main arc4 joydev snd_hda_intel snd_hda_codec rt61pci rt2x00pci rt2x00lib usbhid snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event hid snd_seq snd_timer snd_seq_device psmouse videodev mac80211 cfg80211 snd eeprom_93cx6 soundcore wacom asus_atk0110 serio_raw snd_page_alloc lp parport firewire_ohci firewire_core usb_storage uas r8169 crc_itu_t atl1e pata_marvell ahci libahci
[  261.013764] r8169 0000:05:01.0: eth2: link down
[  262.521283] r8169 0000:05:01.0: eth2: link up
[  306.209855] r8169 0000:05:01.0: eth2: link down
[  307.733195] r8169 0000:05:01.0: eth2: link up
[  309.006593] r8169 0000:05:01.0: eth2: link down
[  310.658543] r8169 0000:05:01.0: eth2: link up
[  354.265936] r8169 0000:05:01.0: eth2: link down
[  355.807416] r8169 0000:05:01.0: eth2: link up
[  357.014007] r8169 0000:05:01.0: eth2: link down
[  358.554598] r8169 0000:05:01.0: eth2: link up
[  402.237983] r8169 0000:05:01.0: eth2: link down
[  403.797721] r8169 0000:05:01.0: eth2: link up
[  405.065949] r8169 0000:05:01.0: eth2: link down
[  406.618256] r8169 0000:05:01.0: eth2: link up
[  450.250086] r8169 0000:05:01.0: eth2: link down
[  452.029218] r8169 0000:05:01.0: eth2: link up
[  453.050001] r8169 0000:05:01.0: eth2: link down
[  454.598237] r8169 0000:05:01.0: eth2: link up
[  498.246081] r8169 0000:05:01.0: eth2: link down
[  499.998635] r8169 0000:05:01.0: eth2: link up
[  501.017960] r8169 0000:05:01.0: eth2: link down
[  502.661895] r8169 0000:05:01.0: eth2: link up
[  546.266024] r8169 0000:05:01.0: eth2: link down
[  547.790008] r8169 0000:05:01.0: eth2: link up
[  549.042040] r8169 0000:05:01.0: eth2: link down
[  550.662765] r8169 0000:05:01.0: eth2: link up
[  594.273971] r8169 0000:05:01.0: eth2: link down
[  595.832656] r8169 0000:05:01.0: eth2: link up
[  597.045935] r8169 0000:05:01.0: eth2: link down
[  598.600725] r8169 0000:05:01.0: eth2: link up
[  642.246050] r8169 0000:05:01.0: eth2: link down
[  643.812514] r8169 0000:05:01.0: eth2: link up
[  645.049977] r8169 0000:05:01.0: eth2: link down
[  646.601473] r8169 0000:05:01.0: eth2: link up
[  690.274000] r8169 0000:05:01.0: eth2: link down
[  691.813506] r8169 0000:05:01.0: eth2: link up
[  693.029977] r8169 0000:05:01.0: eth2: link down
[  694.623355] r8169 0000:05:01.0: eth2: link up
[  738.254015] r8169 0000:05:01.0: eth2: link down
[  739.835141] r8169 0000:05:01.0: eth2: link up

```

---

