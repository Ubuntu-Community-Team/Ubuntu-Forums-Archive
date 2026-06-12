---
title: "PXE install hangs"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by blueyelabs on 2009-12-09
Hi all,

I have a Dell Poweredge 2600 with only a floppy drive and external SCSI CD-ROM. I've tried to get the thing to boot from the cd-rom but to no avail so I've been trying to get PXE booting to work.
I'm using another (fairly old) computer as DHCP and TFTP server. I followed instructions from [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot) (which I found to be a bit incomplete and quite assuming) and from here [https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](https://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install) (much better).
I'm using xinetd rather than the openbsd-inetd purely because the latter didn't work, but then again, neither does the former.

When I boot the Poweredge it gets the ip address by DHCP fine (192.168.0.2). It then flashes a TFTP prompt before that disappears. After that it seems to do absolutely nothing. I've been listening to eth0 with tshark which has revealed a little but I don't really understand what's going wrong:

```

85.014288 DellComp_8e:84:77 -> Broadcast    ARP Who has 192.168.0.1?  Tell 192.168.0.2
 85.014355 3Com_9f:cb:7b -> DellComp_8e:84:77 ARP 192.168.0.1 is at 00:04:76:9f:cb:7b
 85.014414  192.168.0.2 -> 192.168.0.1  TFTP Read Request, File: pxelinux.0\000, Transfer type: octet\000
 85.206533  192.168.0.1 -> 192.168.0.2  TFTP Option Acknowledgement
 85.206621  192.168.0.2 -> 192.168.0.1  TFTP Error Code, Code: Not defined, Message: TFTP Aborted\000
 85.206788  192.168.0.2 -> 192.168.0.1  TFTP Read Request, File: pxelinux.0\000, Transfer type: octet\000
 85.211639  192.168.0.1 -> 192.168.0.2  TFTP Option Acknowledgement
 85.211745  192.168.0.2 -> 192.168.0.1  TFTP Acknowledgement, Block: 0
 85.211859  192.168.0.1 -> 192.168.0.2  TFTP Data Packet, Block: 1 (last)
 85.211923  192.168.0.2 -> 192.168.0.1  TFTP Acknowledgement, Block: 1
 90.203968 3Com_9f:cb:7b -> DellComp_8e:84:77 ARP Who has 192.168.0.2?  Tell 192.168.0.1
 91.203965 3Com_9f:cb:7b -> DellComp_8e:84:77 ARP Who has 192.168.0.2?  Tell 192.168.0.1
 92.203966 3Com_9f:cb:7b -> DellComp_8e:84:77 ARP Who has 192.168.0.2?  Tell 192.168.0.1

```

As quick reference: 192.168.0.1 = DHCP/TFTP server, 192.168.0.2 = PowerEdge 2600.

The last three lines seem to indicate that the PowerEdge is no longer responding? I'm really no expert at this so I can't really tell. I'm also a little confused by a) the TFTP errors and b) why it's not looking for something like
```

pxelinux.0/11:22:33:44:55

```

Instead of /000.

Anyway, the last message was a good while ago and the thing doesn't seem to be responding. Any help would be much appreciated.

---

