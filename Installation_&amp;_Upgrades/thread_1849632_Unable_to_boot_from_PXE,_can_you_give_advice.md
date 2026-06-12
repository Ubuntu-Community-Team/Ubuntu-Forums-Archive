---
title: "Unable to boot from PXE, can you give advice?"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by ProggerPete on 2011-09-24
I'm trying to install Ubuntu on a Dell C400 laptop.

I've set the C400 to boot from network and fired up tftpd on my windows machine.

Looks like the laptop is not connecting properly. In tfptd i see these logs.

```

Rcvd DHCP inform Msg for IP 192.168.1.20, Mac 74:EA:3A:B1:A8:48 [25/09 11:09:56.639]
Rcvd DHCP inform Msg for IP 192.168.1.20, Mac 74:EA:3A:B1:A8:48 [25/09 11:09:59.639]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [25/09 11:10:21.274]
Client requested address 0.0.0.0 [25/09 11:10:21.274]
DHCP: proposed address 192.168.0.2 [25/09 11:10:21.277]
5352 Request 2 not processed [25/09 11:10:21.278]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [25/09 11:10:25.339]
Client requested address 0.0.0.0 [25/09 11:10:25.339]
DHCP: proposed address 192.168.0.2 [25/09 11:10:25.339]
5352 Request 2 not processed [25/09 11:10:25.340]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [25/09 11:10:33.413]
Client requested address 0.0.0.0 [25/09 11:10:33.413]
DHCP: proposed address 192.168.0.2 [25/09 11:10:33.413]
5352 Request 2 not processed [25/09 11:10:33.414]

```

While on the laptop itself it says.

No DHCP or proxy DHCPoffers received

Any tips for what I might be doing wrong?

---

### Post by Dangertux on 2011-09-24
Can you post your dhcpd.conf. That is what I would check first. 

If not verify that your tfpt pxe boot directory structure is correct and at some point there is a default file.

---

### Post by ProggerPete on 2011-09-24
Where is the dhcpd.conf file? I'm looking through the tftpd folder and can't seem to find one.

Here's a screen shot of the dhcp config. [http://ScrnSht.com/imtoxp](http://ScrnSht.com/imtoxp)

The netboot directory is taken directly from i386 at [http://cdimage.ubuntu.com/netboot/oneiric/](http://cdimage.ubuntu.com/netboot/oneiric/)

There is a default directory at netboot\ubuntu-installer\i386\pxelinux.cfg

I copied the prelinux.cfg file from the netboot directory to the tftpd directory.

The netboot directory is in the tftpd directory.

Cheers,
Peter

---

### Post by Dangertux on 2011-09-24
What is the 192.168.1.0 network? Is that your home network? If it is you may wish to disable dhcp temporarily there, also you may wish to tick the box that says bind dhcp to this address 192.168.0.1.

Also this blog article gives a step by step on what you are trying to do using Windows and TFTPd32 which is just the 32bit version of the software you're using. You might check that out of the other two don't fix your issue. [http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows/page/3](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows/page/3)

---

### Post by ProggerPete on 2011-09-24
I've got the lan card on my pc set to 192.168.0.1 as it's IP.

The 192.168.1.x network is my main network that comes via the WIFI network card.

I've tried disabling the wifi card, but get the same result.

Cheers for the link to instructions. They seem identical to the ones I followed at [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot).

I tried running tftpd from C: as mentioned in the instructions you linked to, no diff from that either.

Logs still look basically the same.

Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [25/09 14:15:38.630]
Client requested address 0.0.0.0 [25/09 14:15:38.631]
DHCP: proposed address 192.168.0.2 [25/09 14:15:38.631]
7952 Request 2 not processed [25/09 14:15:38.632]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [25/09 14:15:42.695]
Client requested address 0.0.0.0 [25/09 14:15:42.695]
DHCP: proposed address 192.168.0.2 [25/09 14:15:42.695]
7952 Request 2 not processed [25/09 14:15:42.696]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [25/09 14:15:50.769]
Client requested address 0.0.0.0 [25/09 14:15:50.769]
DHCP: proposed address 192.168.0.2 [25/09 14:15:50.769]
7952 Request 2 not processed [25/09 14:15:50.771]

00:0B:DB:08:F3:EC is the MAC address of the laptop.

---

### Post by ProggerPete on 2011-09-25
I'm now getting further (although I don't know what fixed my earlier problem.) It seems to be getting stuck sending the install files. The logs show.

```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [26/09 09:24:04.150]
Client requested address 0.0.0.0 [26/09 09:24:04.151]
DHCP: proposed address 192.168.0.2 [26/09 09:24:04.151]
772 Request 2 not processed [26/09 09:24:04.152]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [26/09 09:24:12.225]
Previously allocated address 192.168.0.2 acked [26/09 09:24:12.225]
772 Request 2 not processed [26/09 09:24:12.227]
Connection received from 192.168.0.2 on port 2070 [26/09 09:24:12.229]
Read request for file <netboot\pxelinux.0>. Mode octet [26/09 09:24:12.229]
Using local port 63202 [26/09 09:24:12.229]
<netboot\pxelinux.0>: sent 1 blk, 32 bytes in 0 s. 0 blk resent [26/09 09:24:12.229]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [26/09 09:25:26.635]
Client requested address 0.0.0.0 [26/09 09:25:26.635]
DHCP: proposed address 192.168.0.2 [26/09 09:25:26.635]
772 Request 2 not processed [26/09 09:25:26.636]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [26/09 09:25:30.699]
Previously allocated address 192.168.0.2 acked [26/09 09:25:30.699]
772 Request 2 not processed [26/09 09:25:30.701]
Connection received from 192.168.0.2 on port 2070 [26/09 09:25:30.702]
Read request for file <pxelinux.0>. Mode octet [26/09 09:25:30.703]
Using local port 51347 [26/09 09:25:30.703]
<pxelinux.0>: sent 1 blk, 32 bytes in 0 s. 0 blk resent [26/09 09:25:30.703]
```

---

### Post by tgalati4 on 2011-09-26
Check the BIOS.  Sometimes there are additional settings for PXE in the BIOS that need to be set.

---

### Post by ProggerPete on 2011-09-26
No interesting options to play with in the BIOS. It's just PXE or not PXE.

I tried copying the i386 directory into my tfptd directory so that it loads the actual pxelinux.0 the first time, rather than the pointer that was there before.

It now gets further, but dies saying

No DEFAULT or UI configuration directive found

Logs are

```
Rcvd DHCP inform Msg for IP 192.168.1.20, Mac 74:EA:3A:B1:A8:48 [26/09 18:33:05.767]
Rcvd DHCP inform Msg for IP 192.168.1.20, Mac 74:EA:3A:B1:A8:48 [26/09 18:33:08.767]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [26/09 18:33:23.680]
Client requested address 0.0.0.0 [26/09 18:33:23.680]
DHCP: proposed address 192.168.0.2 [26/09 18:33:23.680]
7908 Request 2 not processed [26/09 18:33:23.681]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:0B:DB:08:F3:EC [26/09 18:33:31.753]
Previously allocated address 192.168.0.2 acked [26/09 18:33:31.754]
7908 Request 2 not processed [26/09 18:33:31.755]
Connection received from 192.168.0.2 on port 2070 [26/09 18:33:31.757]
Read request for file <pxelinux.0>. Mode octet [26/09 18:33:31.757]
Using local port 62393 [26/09 18:33:31.757]
<pxelinux.0>: sent 52 blks, 26449 bytes in 0 s. 0 blk resent [26/09 18:33:31.799]
Connection received from 192.168.0.2 on port 49152 [26/09 18:33:31.882]
Read request for file <pxelinux.cfg/44454c4c-0000-1000-8000-80c04f000000>. Mode octet [26/09 18:33:31.882]
File <pxelinux.cfg\44454c4c-0000-1000-8000-80c04f000000> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.883]
Connection received from 192.168.0.2 on port 49153 [26/09 18:33:31.886]
Read request for file <pxelinux.cfg/01-00-0b-db-08-f3-ec>. Mode octet [26/09 18:33:31.886]
File <pxelinux.cfg\01-00-0b-db-08-f3-ec> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.886]
Connection received from 192.168.0.2 on port 49154 [26/09 18:33:31.890]
Read request for file <pxelinux.cfg/C0A80002>. Mode octet [26/09 18:33:31.891]
File <pxelinux.cfg\C0A80002> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.891]
Connection received from 192.168.0.2 on port 49155 [26/09 18:33:31.894]
Read request for file <pxelinux.cfg/C0A8000>. Mode octet [26/09 18:33:31.894]
File <pxelinux.cfg\C0A8000> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.894]
Connection received from 192.168.0.2 on port 49156 [26/09 18:33:31.897]
Read request for file <pxelinux.cfg/C0A800>. Mode octet [26/09 18:33:31.897]
File <pxelinux.cfg\C0A800> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.897]
Connection received from 192.168.0.2 on port 49157 [26/09 18:33:31.901]
Read request for file <pxelinux.cfg/C0A80>. Mode octet [26/09 18:33:31.901]
File <pxelinux.cfg\C0A80> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.901]
Connection received from 192.168.0.2 on port 49158 [26/09 18:33:31.905]
Read request for file <pxelinux.cfg/C0A8>. Mode octet [26/09 18:33:31.905]
File <pxelinux.cfg\C0A8> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.905]
Connection received from 192.168.0.2 on port 49159 [26/09 18:33:31.908]
Read request for file <pxelinux.cfg/C0A>. Mode octet [26/09 18:33:31.908]
File <pxelinux.cfg\C0A> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.908]
Connection received from 192.168.0.2 on port 49160 [26/09 18:33:31.911]
Read request for file <pxelinux.cfg/C0>. Mode octet [26/09 18:33:31.911]
File <pxelinux.cfg\C0> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.911]
Connection received from 192.168.0.2 on port 49161 [26/09 18:33:31.914]
Read request for file <pxelinux.cfg/C>. Mode octet [26/09 18:33:31.914]
File <pxelinux.cfg\C> : error 2 in system call CreateFile The system cannot find the file specified. [26/09 18:33:31.915]
Connection received from 192.168.0.2 on port 49162 [26/09 18:33:31.918]
Read request for file <pxelinux.cfg/default>. Mode octet [26/09 18:33:31.918]
OACK: <tsize=28,> [26/09 18:33:31.918]
Using local port 62404 [26/09 18:33:31.918]
<pxelinux.cfg\default>: sent 1 blk, 28 bytes in 0 s. 0 blk resent [26/09 18:33:31.921]

```

---

### Post by ProggerPete on 2011-09-26
The problem is that the tar contains link files which windows does not understand. Windows makes them text files instead.

If you replace the link files with the files they are linking to everything works.

---

