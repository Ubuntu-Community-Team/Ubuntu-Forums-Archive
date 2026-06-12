---
title: "PXE install: TFTP Open Timeout"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by Beanalby on 2006-04-25
I'm trying a PXE install off a Windows machine, going off of
[https://wiki.ubuntu.com/Installation/WindowsServerNetboot](https://wiki.ubuntu.com/Installation/WindowsServerNetboot)

Set it all up, tftpd32 seems to be working as I can access it from the same machine:

```
C:\Documents and Settings\Administrator>tftp localhost get netboot/pxelinux.0 test
Transfer successful: 11830 bytes in 1 second, 11830 bytes/s

```

powering up the client and booting gives the following in tftp32's log:

```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:B0:D0:A4:B4:BB [25/04 19:42:06.430]
DHCP: proposed address 192.168.1.1 [25/04 19:42:06.430]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:B0:D0:A4:B4:BB [25/04 19:42:08.570]
Previously allocated address acked [25/04 19:42:08.570]
Connection received from 192.168.1.1 on port 2070 [25/04 19:42:08.586]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:42:08.586]
OACK: <tsize=11830,> [25/04 19:42:08.586]
Connection received from 192.168.1.1 on port 2071 [25/04 19:42:10.601]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:42:10.601]
OACK: <tsize=11830,> [25/04 19:42:10.601]
Connection received from 192.168.1.1 on port 2072 [25/04 19:42:14.601]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:42:14.601]
OACK: <tsize=11830,> [25/04 19:42:14.601]
Connection received from 192.168.1.1 on port 2073 [25/04 19:42:20.586]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:42:20.601]
OACK: <tsize=11830,> [25/04 19:42:20.601]
TIMEOUT waiting for Ack block #0  [25/04 19:42:23.586]
TIMEOUT waiting for Ack block #0  [25/04 19:42:25.601]
Connection received from 192.168.1.1 on port 2074 [25/04 19:42:28.555]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:42:28.555]
OACK: <tsize=11830,> [25/04 19:42:28.555]
TIMEOUT waiting for Ack block #0  [25/04 19:42:29.617]
TIMEOUT waiting for Ack block #0  [25/04 19:42:35.601]
Connection received from 192.168.1.1 on port 2075 [25/04 19:42:38.508]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:42:38.508]
TIMEOUT waiting for Ack block #0  [25/04 19:42:43.555]
TIMEOUT waiting for Ack block #1  [25/04 19:42:53.555]
Connection received from 192.168.1.1 on port 2076 [25/04 19:43:14.539]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:43:14.539]
TIMEOUT waiting for Ack block #1  [25/04 19:43:29.539]
Connection received from 192.168.1.1 on port 2077 [25/04 19:44:26.539]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:44:26.570]
TIMEOUT waiting for Ack block #1  [25/04 19:44:41.570]
Connection received from 192.168.1.1 on port 2078 [25/04 19:46:14.539]
Read request for file <\netboot\pxelinux.0>. Mode octet [25/04 19:46:14.539]
TIMEOUT waiting for Ack block #1  [25/04 19:46:29.539]

```

The client just shows "PXE-E32: TFTP open timeout"

So it can get an IP, and it acknowledges the transfer is initiated, but then borks.

Any idea what's causing this?  The client is a Dell Latitude LS, if that helps.

---

### Post by tebibyte on 2007-04-09
same problem.

---

### Post by Darkseren on 2008-02-08
ive been trying to figure this out for about a week now. cant seem to find anything.

```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:E0:B8:53:96:3A [08/02 14:17:05.640]
DHCP: proposed address 192.168.0.110 [08/02 14:17:07.140]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:E0:B8:53:96:3A [08/02 14:17:07.718]
Previously allocated address 192.168.0.110 acked [08/02 14:17:09.218]
Connection received from 192.168.0.110 on port 2070 [08/02 14:17:09.234]
Read request for file <pxelinux.0>. Mode octet [08/02 14:17:09.234]
OACK: <tsize=13156,> [08/02 14:17:09.234]
Using local port 2803 [08/02 14:17:09.234]
Connection received from 192.168.0.110 on port 2071 [08/02 14:17:11.250]
Read request for file <pxelinux.0>. Mode octet [08/02 14:17:11.250]
OACK: <tsize=13156,> [08/02 14:17:11.250]
Using local port 2804 [08/02 14:17:11.265]
Connection received from 192.168.0.110 on port 2072 [08/02 14:17:15.265]
Read request for file <pxelinux.0>. Mode octet [08/02 14:17:15.265]
OACK: <tsize=13156,> [08/02 14:17:15.265]
Using local port 2805 [08/02 14:17:15.265]
Connection received from 192.168.0.110 on port 2073 [08/02 14:17:21.250]
Read request for file <pxelinux.0>. Mode octet [08/02 14:17:21.250]
OACK: <tsize=13156,> [08/02 14:17:21.250]
Using local port 2806 [08/02 14:17:21.250]
TIMEOUT waiting for Ack block #0  [08/02 14:17:24.234]
TIMEOUT waiting for Ack block #0  [08/02 14:17:26.265]
Connection received from 192.168.0.110 on port 2074 [08/02 14:17:29.218]
Read request for file <pxelinux.0>. Mode octet [08/02 14:17:29.218]
OACK: <tsize=13156,> [08/02 14:17:29.218]
Using local port 2809 [08/02 14:17:29.218]
TIMEOUT waiting for Ack block #0  [08/02 14:17:30.265]
TIMEOUT waiting for Ack block #0  [08/02 14:17:36.265]
Connection received from 192.168.0.110 on port 2075 [08/02 14:17:39.156]
Read request for file <pxelinux.0>. Mode octet [08/02 14:17:39.203]
Using local port 2812 [08/02 14:17:39.203]
TIMEOUT waiting for Ack block #0  [08/02 14:17:44.218]
TIMEOUT waiting for Ack block #1  [08/02 14:17:54.234]
Connection received from 192.168.0.110 on port 2076 [08/02 14:18:15.187]
Read request for file <pxelinux.0>. Mode octet [08/02 14:18:15.187]
Using local port 2832 [08/02 14:18:15.187]
TIMEOUT waiting for Ack block #1  [08/02 14:18:30.203]
Connection received from 192.168.0.110 on port 2077 [08/02 14:19:27.187]
Read request for file <pxelinux.0>. Mode octet [08/02 14:19:27.203]
Using local port 2963 [08/02 14:19:27.203]
TIMEOUT waiting for Ack block #1  [08/02 14:19:42.203]

```

---

