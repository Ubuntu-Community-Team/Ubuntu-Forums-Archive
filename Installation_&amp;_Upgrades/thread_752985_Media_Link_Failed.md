---
title: "Media Link Failed"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by abdulkadiradekunle on 2008-04-12
I just installed Linux OpenLab 3.2 as a thinclient server in one of the Computer Laboratories under my care.

After installation, the thinclients in my own Lab boots up and connection to the server was established.

But When I took it the Lab, there were 4 different error messages that I received.

They are:

(1)
Console: switching to color frame buffer device 100x37
ssfd: 2D acceleration is enabled scrolling mode ypan (auto max)
fpo: SiS 630 frame buffer device, version 1.6.32
sisfb (c) 2001-2004 Thomas Winischoffer
pty: 256 unix98 ptys configured
RAMDisk driver initialised: 16 RAM disks of 4096 size 1024 blocksize 
Uniform Multi-Paltform E-IDE driver Revision: 7.00beta4-2.4
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
NET4: Linux TCP/IP 1.0 for NET4.0
IP: Protocols: ICMP, UDP, TCP
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 4096 bind 8192)
NET4: Unix domain sockets 1.0/SMP for Linux NET4.0.
RAMDISK: Compressed image found at block 0
Freeing initrd memory: 1012k freed
VFS: Mounted root (ext2 filesystem).
Mounted devfs on /dev
Freeing unused kernel memory: 88k freed
=============================================================================
Running /linuxrc
Mounting /proc
linuxrc: Installing sis900 driver
modprobe sis900
/sbin/insmod /lib/modules/2.4.26-ltsp-2/kernel/lib/crc32.o
Using /lib/modules/2.4.26-ltsp-2/kernel/lib/crc32.o
Symbol version prefix ''
/sbin/insmod /lib/modules/2.4.26-ltsp-2/kernel/drivers/net/sis900.o
sis900.c: v1.08.06 9/24/2002
PCI: Found IRQ 9 for device 00:01.1
PCI: Sharing IRQ 9 with 00:0d.0
eth0: SiS 900 Internal MII PHY transceiver found at address 1.
eht0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xdc00, IRQ 9, 00:0a:e6:f5:2c:4f.
Running dhcpd on port 67
eth0: Media Link Off


ERROR! dhcpd failed!

Kernel panic: Attempted to kill init!

(2)
"already registered at priority 0
				 error opening security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Fatal server error: could not open default font 'fixed' 
Please consult the The X.Org Foundation support [http://wiki.X.Org](http://wiki.X.Org) for help.
Please also check the log file at "/var/log/Xorg.0.0.log" for additional information
xserver failed, press <enter> to continue _

(3)
probing... [RTL8139]Found Realtek 8139 ROM address 0xff80
- ioaddr 0xD800, addr 00:57:FF:0D:46:65 100Mbps full duplex
Searching for server (DHCP)...
..Me: 192.168.0.246, Server: 192.168.0.254, Gateway 192.168.0.254
Loading 192.168.0.254:/lts/Vmlinuz-2.4.26-ltsp-2 .mounting /lts: Permission denied
Unable to load file
<sleep>
<abort>

The message above is displayed on some of the cards




Some of the clients that boots up could not login due to dcopserver problem, it was confirm to be running on the server. other sessions like Gnome are also not loading. the error message was:

(4)
There was an error setting up inter-process communications for KDE. The message returned by the system was:
Could not read network connection list.
/home/username/.DCOPserver_Hostname_ws33_0

Please check that the "dcopserver" program is running!

after trying to reinstall the kde from the client's end, the following was displayed:

Could not start ksmserver. Check your installation.



Please help me out.

Thank you

---

