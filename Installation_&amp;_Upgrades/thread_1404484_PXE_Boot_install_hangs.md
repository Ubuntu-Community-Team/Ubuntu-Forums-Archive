---
title: "PXE Boot install hangs"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by ricgar on 2010-02-11
Hi
 
I am attemptiong to do PXE boot install to a machine that has no optical drive and doesn't support usb installations.
 
I have setup a TFTP server with DHCP all works well when i test it on a laptop, but if i attempt it on a desktop, then it loads the default file and then turns to a blank screen and the machine halts completely, with no more anything from the machine, not even keyboard response after it.
 
if i check the TFTP server logs, this is what i get:
 
```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:E0:18:AA:94:DE [11/02 20:31:47.572]
DHCP: proposed address 194.168.2.50 [11/02 20:31:49.087]
5832 Request 2 not processed [11/02 20:31:49.134]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:E0:18:AA:94:DE [11/02 20:31:49.572]
Previously allocated address 194.168.2.50 acked [11/02 20:31:51.072]
Connection received from 194.168.2.50 on port 2070 [11/02 20:31:51.087]
Read request for file <pxelinux.0>. Mode octet [11/02 20:31:51.087]
OACK: <tsize=14776,> [11/02 20:31:51.103]
Using local port 1371 [11/02 20:31:51.103]
5832 Request 2 not processed [11/02 20:31:51.150]
Peer returns ERROR <TFTP Aborted> -> aborting transfer [11/02 20:31:51.197]
Connection received from 194.168.2.50 on port 2071 [11/02 20:31:51.197]
Read request for file <pxelinux.0>. Mode octet [11/02 20:31:51.197]
Using local port 1372 [11/02 20:31:51.197]
<pxelinux.0>: sent 29 blks, 14776 bytes in 0 s. 0 blk resent [11/02 20:31:51.322]
Connection received from 194.168.2.50 on port 57089 [11/02 20:31:51.337]
Read request for file <pxelinux.cfg/00000000-0000-0000-0000-000000000000>. Mode octet [11/02 20:31:51.337]
File <pxelinux.cfg\00000000-0000-0000-0000-000000000000> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.337]
Connection received from 194.168.2.50 on port 57090 [11/02 20:31:51.337]
Read request for file <pxelinux.cfg/01-00-e0-18-aa-94-de>. Mode octet [11/02 20:31:51.337]
File <pxelinux.cfg\01-00-e0-18-aa-94-de> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.337]
Connection received from 194.168.2.50 on port 57091 [11/02 20:31:51.337]
Read request for file <pxelinux.cfg/C2A80232>. Mode octet [11/02 20:31:51.353]
File <pxelinux.cfg\C2A80232> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.353]
Connection received from 194.168.2.50 on port 57092 [11/02 20:31:51.353]
Read request for file <pxelinux.cfg/C2A8023>. Mode octet [11/02 20:31:51.353]
File <pxelinux.cfg\C2A8023> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.353]
Connection received from 194.168.2.50 on port 57093 [11/02 20:31:51.353]
Read request for file <pxelinux.cfg/C2A802>. Mode octet [11/02 20:31:51.353]
File <pxelinux.cfg\C2A802> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.353]
Connection received from 194.168.2.50 on port 57094 [11/02 20:31:51.353]
Read request for file <pxelinux.cfg/C2A80>. Mode octet [11/02 20:31:51.353]
File <pxelinux.cfg\C2A80> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.368]
Connection received from 194.168.2.50 on port 57095 [11/02 20:31:51.368]
Read request for file <pxelinux.cfg/C2A8>. Mode octet [11/02 20:31:51.368]
File <pxelinux.cfg\C2A8> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.368]
Connection received from 194.168.2.50 on port 57096 [11/02 20:31:51.368]
Read request for file <pxelinux.cfg/C2A>. Mode octet [11/02 20:31:51.368]
File <pxelinux.cfg\C2A> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.368]
Connection received from 194.168.2.50 on port 57097 [11/02 20:31:51.368]
Read request for file <pxelinux.cfg/C2>. Mode octet [11/02 20:31:51.368]
File <pxelinux.cfg\C2> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.368]
Connection received from 194.168.2.50 on port 57098 [11/02 20:31:51.368]
Read request for file <pxelinux.cfg/C>. Mode octet [11/02 20:31:51.368]
File <pxelinux.cfg\C> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.368]
Connection received from 194.168.2.50 on port 57099 [11/02 20:31:51.368]
Read request for file <pxelinux.cfg/default>. Mode octet [11/02 20:31:51.368]
OACK: <tsize=127,> [11/02 20:31:51.384]
Using local port 1383 [11/02 20:31:51.384]
<pxelinux.cfg\default>: sent 1 blk, 127 bytes in 0 s. 0 blk resent [11/02 20:31:51.462]
Connection received from 194.168.2.50 on port 57100 [11/02 20:31:51.462]
Read request for file <ubuntu-installer/i386/boot-screens/menu.cfg>. Mode octet [11/02 20:31:51.462]
OACK: <tsize=813,> [11/02 20:31:51.462]
Using local port 1384 [11/02 20:31:51.462]
Connection received from 194.168.2.50 on port 57101 [11/02 20:31:51.525]
<ubuntu-installer\i386\boot-screens\menu.cfg>: sent 2 blks, 813 bytes in 0 s. 0 blk resent [11/02 20:31:51.525]
Read request for file <ubuntu-installer/i386/boot-screens/stdmenu.cfg>. Mode octet [11/02 20:31:51.525]
OACK: <tsize=395,> [11/02 20:31:51.525]
Using local port 1385 [11/02 20:31:51.525]
<ubuntu-installer\i386\boot-screens\stdmenu.cfg>: sent 1 blk, 395 bytes in 0 s. 0 blk resent [11/02 20:31:51.681]
Connection received from 194.168.2.50 on port 57102 [11/02 20:31:51.681]
Read request for file <ubuntu-installer/i386/boot-screens/text.cfg>. Mode octet [11/02 20:31:51.681]
OACK: <tsize=401,> [11/02 20:31:51.681]
Using local port 1386 [11/02 20:31:51.681]
<ubuntu-installer\i386\boot-screens\text.cfg>: sent 1 blk, 401 bytes in 0 s. 0 blk resent [11/02 20:31:51.728]
Connection received from 194.168.2.50 on port 57103 [11/02 20:31:51.743]
Read request for file <ubuntu-installer/i386/boot-screens/amdtext.cfg>. Mode octet [11/02 20:31:51.743]
File <ubuntu-installer\i386\boot-screens\amdtext.cfg> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.743]
Connection received from 194.168.2.50 on port 57104 [11/02 20:31:51.743]
Read request for file <ubuntu-installer/i386/boot-screens/gtk.cfg>. Mode octet [11/02 20:31:51.743]
File <ubuntu-installer\i386\boot-screens\gtk.cfg> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.743]
Connection received from 194.168.2.50 on port 57105 [11/02 20:31:51.743]
Read request for file <ubuntu-installer/i386/boot-screens/amdgtk.cfg>. Mode octet [11/02 20:31:51.743]
File <ubuntu-installer\i386\boot-screens\amdgtk.cfg> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:51.743]
Connection received from 194.168.2.50 on port 57106 [11/02 20:31:51.743]
Read request for file <ubuntu-installer/i386/boot-screens/stdmenu.cfg>. Mode octet [11/02 20:31:51.743]
OACK: <tsize=395,> [11/02 20:31:51.743]
Using local port 1390 [11/02 20:31:51.743]
<ubuntu-installer\i386\boot-screens\stdmenu.cfg>: sent 1 blk, 395 bytes in 0 s. 0 blk resent [11/02 20:31:51.837]
Connection received from 194.168.2.50 on port 57107 [11/02 20:31:51.837]
Read request for file <ubuntu-installer/i386/boot-screens/adtext.cfg>. Mode octet [11/02 20:31:51.853]
OACK: <tsize=566,> [11/02 20:31:51.853]
Using local port 1392 [11/02 20:31:51.853]
Connection received from 194.168.2.50 on port 57108 [11/02 20:31:51.993]
Read request for file <ubuntu-installer/i386/boot-screens/adamdtext.cfg>. Mode octet [11/02 20:31:52.009]
File <ubuntu-installer\i386\boot-screens\adamdtext.cfg> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:52.009]
Connection received from 194.168.2.50 on port 57109 [11/02 20:31:52.009]
Read request for file <ubuntu-installer/i386/boot-screens/adgtk.cfg>. Mode octet [11/02 20:31:52.009]
File <ubuntu-installer\i386\boot-screens\adgtk.cfg> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:52.009]
Connection received from 194.168.2.50 on port 57110 [11/02 20:31:52.009]
Read request for file <ubuntu-installer/i386/boot-screens/adamdgtk.cfg>. Mode octet [11/02 20:31:52.009]
File <ubuntu-installer\i386\boot-screens\adamdgtk.cfg> : error 2 in system call CreateFile The system cannot find the file specified. [11/02 20:31:52.009]
Connection received from 194.168.2.50 on port 57111 [11/02 20:31:52.009]
Read request for file <ubuntu-installer/i386/boot-screens/vesamenu.c32>. Mode octet [11/02 20:31:52.009]
OACK: <tsize=144392,> [11/02 20:31:52.009]
Using local port 1396 [11/02 20:31:52.009]
<ubuntu-installer\i386\boot-screens\adtext.cfg>: sent 2 blks, 566 bytes in 1 s. 0 blk resent [11/02 20:31:52.009]
<ubuntu-installer\i386\boot-screens\vesamenu.c32>: sent 283 blks, 144392 bytes in 0 s. 0 blk resent [11/02 20:31:52.134]
Connection received from 194.168.2.50 on port 57112 [11/02 20:31:52.509]
Read request for file <pxelinux.cfg/default>. Mode octet [11/02 20:31:52.509]
OACK: <tsize=127,> [11/02 20:31:52.509]
Using local port 1397 [11/02 20:31:52.509]
TIMEOUT waiting for Ack block #0  [11/02 20:32:07.572]

```
 
Any idea why it hangs after it seems to load vesamenu.c32?
 
Any help greatly appreciated.
 
Thanks

---

