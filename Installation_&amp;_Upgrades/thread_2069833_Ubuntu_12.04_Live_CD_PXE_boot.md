---
title: "Ubuntu 12.04 Live CD PXE boot"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by pdhingra on 2012-10-11
I am trying to setup PXE boot for Ubuntu live CD. This is a customized  version of Ubuntu 12.04 created using remastersys backup option

As the server, I have a Windows 7 machine: using TFTPD version 4.00 and haneWIN NFS server 1.2.6

IP of this server is 198.168.1.1

This is what my pxe config looks like

      kernel sdi-backup/casper/vmlinuz
      append boot=casper netboot=nfs nfsroot=192.168.1.1:/sdi initrd=sdi-backup/casper/initrd.gz -- verbose

This is my NFS exports file
C:\tftp\netboot\sdi-backup -name:sdi -maproot:0 -range 192.168.1.10 192.168.1.20

My TFTP server settings are:
[IMG]http://i48.tinypic.com/24d1ylt.jpg[/IMG]

My DHCP server settings are:
[IMG]http://i47.tinypic.com/2l8ku2r.jpg[/IMG]

Note that even though screenshot contains a 192.168.0.6 interface  address, I disable that interface before I test. Only active interface  is 192.168.1.1 and there is no other DHCP server on the network. In  fact, network consists of these two machine connected directly to each  other.

When the other machine on the networks boots up, it is able to find the servers and loads vmlinuz and initrd correctly.

As further booting starts, the client machine shows this message

IP-Config: no response after 3 seconds - giving up
IP-Config: eth0 hardware address [MAC address] mtu 1500 DHCP RARP

This message gets repeated with increasing value of time and then there is a kernel panic since booting cannot continue.

The server on the other hand shows these messages

<netboot\sdi-backup\casper\initrd.gz>: sent 39540 blks, 20244389 bytes in 19 s. 0 blk resent [11/10 10:30:07.887]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac [MAC Addr] [11/10 10:30:16.200]
Client requested address 0.0.0.80 [11/10 10:30:16.200]
DHCP: proposed address 192.168.1.10 [11/10 10:30:16.200]
5920 Request 2 not processed [11/10 10:30:16.202]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac [MAC Addr]  [11/10 10:30:17.205]
Client requested address 0.0.0.80 [11/10 10:30:17.205]
DHCP: proposed address 192.168.1.10 [11/10 10:30:17.205]
5920 Request 2 not processed [11/10 10:30:17.208]
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac [MAC Addr]  [11/10 10:30:20.987]
Client requested address 0.0.0.80 [11/10 10:30:20.988]
DHCP: proposed address 192.168.1.10 [11/10 10:30:20.988]
5920 Request 2 not processed [11/10 10:30:20.990]

Please help me figure out what is going wrong here and how can I get this PXE boot working.

---

### Post by dominictorreto87 on 2012-10-11
I think that your client is in a different subnet, please check

Timeout 20-30sek
tick option negotiation
bind DHCP address: 192.168.1.10

---

### Post by pdhingra on 2012-10-11
> **dominictorreto87 said:**
> I think that your client is in a different subnet, please check

Timeout 20-30sek
tick option negotiation
bind DHCP address: 192.168.1.10

The two machines are directly connected, both of them are on the same subnet. In fact kernel boots up fine. It is further booting that is getting messed up.
Also negotiation and PXE boot are mutually exclusive options

---

### Post by xicarusx on 2012-12-06
Your problem is in the NFS support for versions 12.04 and up. In order to get it to boot the way you want to follow this guide.

[http://random.kakaopor.hu/ubuntu-12-04-live-nfspxe-boot-diskless-casper-kept](http://random.kakaopor.hu/ubuntu-12-04-live-nfspxe-boot-diskless-casper-kept)

You could also run an Ubuntu PXE Server in a VM on Windows. I don't like the windows tftp32. I have a guide on setting up a proper PXE server if you are interested.

---

