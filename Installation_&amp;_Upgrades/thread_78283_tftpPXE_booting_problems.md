---
title: "tftp/PXE booting problems"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by stuporglue on 2005-10-18
Hi there, 

I'm trying to setup a PXE boot setup so I can write one simple, clear and concise wiki tutorial.

I have dhcp3-server and tftpd-hpa installed. 

I have tested the dhcp server with a Knoppix disk on the target comptuer, and it works correctly. 

tftp works on localhost, but not from Knoppix. Here's  what happens...

```
$ tftp 192.168.1.0
tftp>get pxelinux.0
sendto: permission denied
tftp>
```

Once I quit tftp, an empty (0 bytes) file named pxelinux.0 exists, but that's it. 

Syslog on the server for this time period shows
```

eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
BOOTREQUEST from 00:08:74:02:52:3f via eth0
BOOTREPLY on 192.168.1.248 to 00:08:74:02:52:3f via eth0
RRQ from 192.168.1.248 filename pxelinux.0
    #   It hangs here untill I power down the machine
eth0: link down

```

Does anyone know why pxelinux.0 can't be read over the network? It works fine on the server's localhost.

---

### Post by insanity on 2005-10-24
Hi! 

im new here (and to ubuntu), but i got the same problem!

1. client booting. 
2. dhcp is working like it should
3. but then, tftp gets a "open timeout"

i tried to connect locally to the server

```
insanity@matrix:/$ tftp 192.168.0.1
tftp> get pxelinux.0
tftp: pxelinux.0: Permission denied
tftp>

```

as you see, it doesn't work either. so it has to be the tftpd.
but i don't know what i should do about that.

i think thats the same problem.
i would really apreciate help. 

thanks
insanity

---

### Post by rgmussel on 2006-04-20
I don't know if you are still working on this, but one of the things I discovered is that the ownership of the file must be set to "nobody:nogroup". I hope that helps.

---

