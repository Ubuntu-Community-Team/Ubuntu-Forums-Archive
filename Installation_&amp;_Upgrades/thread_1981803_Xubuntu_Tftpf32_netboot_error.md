---
title: "Xubuntu Tftpf32 netboot error"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by eclipsegaze on 2012-05-17
So over the last few days I've been struggling to network install xubuntu onto an old Toshiba that lacks a cd drive and a bootable usb. I am using the alternative xubuntu extracted image and I have configured everything according to the suggestions in this article    [http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)   but my Tfpd32 server keeps exploding and says this

Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:08:0D:AA:7A:DC [17/05 12:28:04.187]
DHCP: proposed address 192.168.1.4 [17/05 12:28:04.187]
3220 Request 2 not processed [17/05 12:28:04.250]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:08:0D:AA:7A:DC [17/05 12:28:06.250]
Previously allocated address 192.168.1.4 acked [17/05 12:28:06.250]
Connection received from 192.168.1.4 on port 2070 [17/05 12:28:06.250]
Read request for file <pxelinux.0>. Mode octet [17/05 12:28:06.250]
Using local port 4615 [17/05 12:28:06.250]
3220 Request 2 not processed [17/05 12:28:06.296]
<pxelinux.0>: sent 52 blks, 26461 bytes in 0 s. 0 blk resent [17/05 12:28:06.375]
Connection received from 192.168.1.4 on port 49152 [17/05 12:28:06.437]
Read request for file <pxelinux.cfg/ceab0800-bfd9-11d3-8020-ad1523026905>. Mode octet [17/05 12:28:06.453]
File <pxelinux.cfg/ceab0800-bfd9-11d3-8020-ad1523026905> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.453]
Connection received from 192.168.1.4 on port 49153 [17/05 12:28:06.453]
Read request for file <pxelinux.cfg/01-00-08-0d-aa-7a-dc>. Mode octet [17/05 12:28:06.453]
File <pxelinux.cfg/01-00-08-0d-aa-7a-dc> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.453]
Connection received from 192.168.1.4 on port 49154 [17/05 12:28:06.453]
Read request for file <pxelinux.cfg/C0A80104>. Mode octet [17/05 12:28:06.453]
File <pxelinux.cfg/C0A80104> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.453]
Connection received from 192.168.1.4 on port 49155 [17/05 12:28:06.453]
Read request for file <pxelinux.cfg/C0A8010>. Mode octet [17/05 12:28:06.468]
File <pxelinux.cfg/C0A8010> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.468]
Connection received from 192.168.1.4 on port 49156 [17/05 12:28:06.468]
Read request for file <pxelinux.cfg/C0A801>. Mode octet [17/05 12:28:06.468]
File <pxelinux.cfg/C0A801> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.468]
Connection received from 192.168.1.4 on port 49157 [17/05 12:28:06.468]
Read request for file <pxelinux.cfg/C0A80>. Mode octet [17/05 12:28:06.468]
File <pxelinux.cfg/C0A80> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.468]
Connection received from 192.168.1.4 on port 49158 [17/05 12:28:06.468]
Read request for file <pxelinux.cfg/C0A8>. Mode octet [17/05 12:28:06.468]
File <pxelinux.cfg/C0A8> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.484]
Connection received from 192.168.1.4 on port 49159 [17/05 12:28:06.484]
Read request for file <pxelinux.cfg/C0A>. Mode octet [17/05 12:28:06.484]
File <pxelinux.cfg/C0A> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.484]
Connection received from 192.168.1.4 on port 49160 [17/05 12:28:06.484]
Read request for file <pxelinux.cfg/C0>. Mode octet [17/05 12:28:06.484]
File <pxelinux.cfg/C0> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.484]
Connection received from 192.168.1.4 on port 49161 [17/05 12:28:06.484]
Read request for file <pxelinux.cfg/C>. Mode octet [17/05 12:28:06.484]
File <pxelinux.cfg/C> : error 2 in system call CreateFile The system cannot find the file specified. [17/05 12:28:06.484]
Connection received from 192.168.1.4 on port 49162 [17/05 12:28:06.500]
Read request for file <pxelinux.cfg/default>. Mode octet [17/05 12:28:06.500]
OACK: <tsize=28,> [17/05 12:28:06.500]
Using local port 4626 [17/05 12:28:06.500]
<pxelinux.cfg/default>: sent 1 blk, 28 bytes in 0 s. 0 blk resent [17/05 12:28:06.546]

and on the laptop I'm trying to install to after appearing to be going well the last thing it says is this..

Trying to load: pxelinux.cfg/default                                                                                      ok
No Default or UI configuration directive found!
boot: _

but this is bull because I've checked default which is inside the pxelinux.cfg folder and it points to ../boot-screens/syslinux.cfg which totally exists and everything. I have all the permissions set to let everything do whatever they want. Please somebody help!

---

### Post by eclipsegaze on 2012-05-18
Somebody?

---

