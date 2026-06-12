---
title: "PXE Problems"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by thon0925 on 2007-12-12
Hi, I have a cheap Emachines PC and am having problems PXE booting. I am using another computer with Windows with the program tftpd working. The computer boots and the default Ubuntu installer starts. I select Ubuntu desktop and it installs with no problems, but when I reboot a text only screen shows up in which I can do basic commands such as login. I tried this with Gusty Gibbon and Feisty Fawn with the same problem on both.

---

### Post by daengbo on 2007-12-13
I'm sorry. I don't understand. Are you doing a network install? What about the PXE boot is not working? Are you trying to use the EMachines box as a thin client?

Please give full details so we can help.

---

### Post by thon0925 on 2007-12-13
I have two Emachines one with the DHCP server that sends the PXE installer and one I that I'm trying to install Gusty Gibbon (A full install of the GUI and features). The installer starts through PXE and seems to install everything with no problem, but when I restart it is a command line interface.
heres a log of the PXE starting using tftpd32.exe ```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:40:CA:21:56:56 [13/12 16:11:08.262]
DHCP: proposed address 192.168.1.8 [13/12 16:11:09.856]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:40:CA:21:56:56 [13/12 16:11:10.262]
Previously allocated address 192.168.1.8 acked [13/12 16:11:11.762]
Connection received from 192.168.1.8 on port 2070 [13/12 16:11:12.294]
Read request for file <\netboot\pxelinux.0>. Mode octet [13/12 16:11:12.294]
OACK: <tsize=13156,> [13/12 16:11:12.294]
Using local port 3589 [13/12 16:11:12.294]
Connection received from 192.168.1.8 on port 2071 [13/12 16:11:12.294]
Peer returns ERROR <TFTP Aborted> -> aborting transfer [13/12 16:11:12.294]
Read request for file <\netboot\pxelinux.0>. Mode octet [13/12 16:11:12.294]
OACK: <blksize=1456,> [13/12 16:11:12.294]
Using local port 3590 [13/12 16:11:12.294]
<\netboot\pxelinux.0>: sent 10 blks, 13156 bytes in 2 s. 0 blk resent [13/12 16:11:14.294]
Connection received from 192.168.1.8 on port 57089 [13/12 16:11:14.356]
Read request for file <\netboot\pxelinux.cfg/01-00-40-ca-21-56-56>. Mode octet [13/12 16:11:14.356]
File <\netboot\pxelinux.cfg\01-00-40-ca-21-56-56> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.356]
Connection received from 192.168.1.8 on port 57090 [13/12 16:11:14.356]
Read request for file <\netboot\pxelinux.cfg/C0A80108>. Mode octet [13/12 16:11:14.356]
File <\netboot\pxelinux.cfg\C0A80108> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.356]
Connection received from 192.168.1.8 on port 57091 [13/12 16:11:14.387]
Read request for file <\netboot\pxelinux.cfg/C0A8010>. Mode octet [13/12 16:11:14.387]
File <\netboot\pxelinux.cfg\C0A8010> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.387]
Connection received from 192.168.1.8 on port 57092 [13/12 16:11:14.387]
Read request for file <\netboot\pxelinux.cfg/C0A801>. Mode octet [13/12 16:11:14.387]
File <\netboot\pxelinux.cfg\C0A801> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.387]
Connection received from 192.168.1.8 on port 57093 [13/12 16:11:14.403]
Read request for file <\netboot\pxelinux.cfg/C0A80>. Mode octet [13/12 16:11:14.403]
File <\netboot\pxelinux.cfg\C0A80> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.403]
Connection received from 192.168.1.8 on port 57094 [13/12 16:11:14.403]
Read request for file <\netboot\pxelinux.cfg/C0A8>. Mode octet [13/12 16:11:14.403]
File <\netboot\pxelinux.cfg\C0A8> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.403]
Connection received from 192.168.1.8 on port 57095 [13/12 16:11:14.419]
Read request for file <\netboot\pxelinux.cfg/C0A>. Mode octet [13/12 16:11:14.419]
File <\netboot\pxelinux.cfg\C0A> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.419]
Connection received from 192.168.1.8 on port 57096 [13/12 16:11:14.419]
Read request for file <\netboot\pxelinux.cfg/C0>. Mode octet [13/12 16:11:14.419]
File <\netboot\pxelinux.cfg\C0> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.419]
Connection received from 192.168.1.8 on port 57097 [13/12 16:11:14.434]
Read request for file <\netboot\pxelinux.cfg/C>. Mode octet [13/12 16:11:14.434]
File <\netboot\pxelinux.cfg\C> : error 2 in system call CreateFile The system cannot find the file specified. [13/12 16:11:14.434]
Connection received from 192.168.1.8 on port 57098 [13/12 16:11:14.450]
Read request for file <\netboot\pxelinux.cfg/default>. Mode octet [13/12 16:11:14.450]
OACK: <tsize=1527,blksize=1440,> [13/12 16:11:14.450]
Using local port 3600 [13/12 16:11:14.450]
Connection received from 192.168.1.8 on port 57098 [13/12 16:11:15.122]
Read request for file <\netboot\pxelinux.cfg/default>. Mode octet [13/12 16:11:15.122]
OACK: <tsize=1527,blksize=1440,> [13/12 16:11:15.122]
Using local port 3601 [13/12 16:11:15.122]
Connection received from 192.168.1.8 on port 57099 [13/12 16:11:15.137]
<\netboot\pxelinux.cfg\default>: sent 2 blks, 1527 bytes in 1 s. 0 blk resent [13/12 16:11:15.137]
Read request for file <\netboot\ubuntu-installer/i386/boot-screens/boot.txt>. Mode octet [13/12 16:11:15.137]
OACK: <tsize=301,blksize=1440,> [13/12 16:11:15.137]
Using local port 3602 [13/12 16:11:15.137]
Connection received from 192.168.1.8 on port 57099 [13/12 16:11:15.778]
Read request for file <\netboot\ubuntu-installer/i386/boot-screens/boot.txt>. Mode octet [13/12 16:11:15.778]
OACK: <tsize=301,blksize=1440,> [13/12 16:11:15.778]
Using local port 3603 [13/12 16:11:15.778]
<\netboot\ubuntu-installer\i386\boot-screens\boot.txt>: sent 1 blk, 301 bytes in 0 s. 0 blk resent [13/12 16:11:15.794]
Connection received from 192.168.1.8 on port 57100 [13/12 16:11:15.794]
Read request for file <\netboot\ubuntu-installer/i386/boot-screens/splash.rle>. Mode octet [13/12 16:11:15.794]
OACK: <tsize=8023,blksize=1440,> [13/12 16:11:15.794]
Using local port 3604 [13/12 16:11:15.794]
Connection received from 192.168.1.8 on port 57100 [13/12 16:11:16.419]
Read request for file <\netboot\ubuntu-installer/i386/boot-screens/splash.rle>. Mode octet [13/12 16:11:16.434]
OACK: <tsize=8023,blksize=1440,> [13/12 16:11:16.434]
Using local port 3605 [13/12 16:11:16.434]
<\netboot\ubuntu-installer\i386\boot-screens\splash.rle>: sent 6 blks, 8023 bytes in 1 s. 0 blk resent [13/12 16:11:16.497]
TIMEOUT waiting for Ack block #0  [13/12 16:11:30.137]
Connection received from 192.168.1.8 on port 57101 [13/12 16:11:30.137]
Connection received from 192.168.1.8 on port 57101 [13/12 16:11:30.137]
Connection received from 192.168.1.8 on port 57101 [13/12 16:11:30.137]
Connection received from 192.168.1.8 on port 57101 [13/12 16:11:30.137]
Connection received from 192.168.1.8 on port 57101 [13/12 16:11:30.137]
Read request for file <\netboot\ubuntu-installer/i386/linux>. Mode octet [13/12 16:11:30.137]
OACK: <tsize=1745100,blksize=1440,> [13/12 16:11:30.137]
Using local port 3606 [13/12 16:11:30.137]
Read request for file <\netboot\ubuntu-installer/i386/linux>. Mode octet [13/12 16:11:30.137]
OACK: <tsize=1745100,blksize=1440,> [13/12 16:11:30.137]
Using local port 3607 [13/12 16:11:30.137]
Read request for file <\netboot\ubuntu-installer/i386/linux>. Mode octet [13/12 16:11:30.137]
OACK: <tsize=1745100,blksize=1440,> [13/12 16:11:30.137]
Using local port 3608 [13/12 16:11:30.137]
Read request for file <\netboot\ubuntu-installer/i386/linux>. Mode octet [13/12 16:11:30.153]
OACK: <tsize=1745100,blksize=1440,> [13/12 16:11:30.153]
Using local port 3609 [13/12 16:11:30.153]
Read request for file <\netboot\ubuntu-installer/i386/linux>. Mode octet [13/12 16:11:30.153]
OACK: <tsize=1745100,blksize=1440,> [13/12 16:11:30.153]
Using local port 3610 [13/12 16:11:30.153]
TIMEOUT waiting for Ack block #0  [13/12 16:11:30.794]
TIMEOUT waiting for Ack block #0  [13/12 16:11:31.497]
Ack block 24 ignored (received twice) [13/12 16:11:34.919]
Ack block 24 ignored (received twice) [13/12 16:11:34.919]
<\netboot\ubuntu-installer\i386\linux>: sent 1212 blks, 1745100 bytes in 7 s. 2 blks resent [13/12 16:11:37.247]
Connection received from 192.168.1.8 on port 57102 [13/12 16:11:37.247]
Read request for file <\netboot\ubuntu-installer/i386/initrd.gz>. Mode octet [13/12 16:11:37.247]
OACK: <tsize=7003942,blksize=1440,> [13/12 16:11:37.247]
Using local port 3611 [13/12 16:11:37.247]
Connection received from 192.168.1.8 on port 57102 [13/12 16:11:37.903]
Read request for file <\netboot\ubuntu-installer/i386/initrd.gz>. Mode octet [13/12 16:11:37.903]
OACK: <tsize=7003942,blksize=1440,> [13/12 16:11:37.903]
Using local port 3612 [13/12 16:11:37.903]
<\netboot\ubuntu-installer\i386\initrd.gz>: sent 4864 blks, 7003942 bytes in 7 s. 0 blk resent [13/12 16:11:44.169]
TIMEOUT waiting for Ack block #0  [13/12 16:11:45.137]
TIMEOUT waiting for Ack block #0  [13/12 16:11:45.153]
TIMEOUT waiting for Ack block #0  [13/12 16:11:45.153]
TIMEOUT waiting for Ack block #0  [13/12 16:11:45.794]
TIMEOUT waiting for Ack block #0  [13/12 16:11:54.903]

```

---

### Post by miksmi on 2007-12-13
Either the desktop didn't load/start or didn't install. To install:

sudo apt-get install ubuntu-desktop

---

### Post by thon0925 on 2007-12-13
Thanks, that did the trick.

---

