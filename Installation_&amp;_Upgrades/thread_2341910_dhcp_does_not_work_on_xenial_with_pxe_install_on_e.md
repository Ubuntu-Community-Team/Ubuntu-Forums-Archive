---
title: "dhcp does not work on xenial with pxe install on eth1"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by allanj on 2016-11-02
Hi

I am setting up an automated install service for several Linuxes, and the setup for trusty is working perfectly, but there is a strange problem with xenial.

This is servers with 2 Network Cards, so I have to specify "interface=eth1" as an argument in the pxe file, and what happens is that the kernel and initrd is loaded correctly, but when it starts up, it can not find the Network. I have access to the DHCP server, so i can see it recieving the DHCPDISCOVER, and it responds with a DHCPOFFER, but that is never recieved on the server it seems.

The server recieves the correct DHCP address during boot, so I can rule out hardware problems, it has to do with the xenial install image, and as I wrote at the start it works fine with trusty.... 

I think it could be apparmor that causes problems, but does anyone know if that could be the case, and if it is, then how do i disable it ?

Best regards
Allan Jacobsen
Linux consultant

---

### Post by allanj on 2016-11-07
Update:

After trying to debug this, I just gave the client a static IP, and the rest of the installation worked perfectly. After reboot the client also Works fine, it still has the static ip, and I can run "apt update" etc. but if I change the Network Card (eth1) to dhcp and reboot, then it does not get an IP address, so it seems to be a general networking problem, not just an install problem. 

The fact that it gets the DHCP address under the PXE negotiation at the start of the install is not a help, because then the Network Card is driven by the firmware, it is when the Linux kernel takes over the problem Begins.....

---

