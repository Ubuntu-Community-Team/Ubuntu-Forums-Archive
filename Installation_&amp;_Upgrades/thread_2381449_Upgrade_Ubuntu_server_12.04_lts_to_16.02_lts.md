---
title: "Upgrade Ubuntu server 12.04 lts to 16.02 lts"
date: 2017-12-31
forum: Installation &amp; Upgrades
---

### Post by patdundee on 2017-12-31
I am upgrading Ubuntu from 12.04 LTS through to 16.04 LTS To do this I have upgraded to 14.04 LTS first Since upgrading to 14.04 I have lost my network and the system cannot even ping its on IP and replies with network unreachable

  When i try 
  ```
ifdown eth0 && ifup eth0

```  I get the following
  ```
ifdown rth0 not configured
/bin/sh: ip: command not found
failed to bring up eth0

```  When i run ifconfig -a it tells me that eth0 has no ip or other details configured However when i check /etc/network/interfaces it is actually configure correct with 

  ```
auto lo eth0 eth0:1
iface lo inet loopback

iface eth0 inet static
address 109.x.x.x The IP
netmask 255.x.x.x The netmask
network 109.x.x.x The network
broadcast 109.x.x.x The Broadcast IP
gateway 109.x.x.x The Gateway

```  Any ideas on what has happened here or how to get around this.  Obviously i cannot use apt as i have no network but i have downloaded  the 14.04 image onto cd
  Many thanks P

---

### Post by TheFu on 2017-12-31
Comments need to be on separate lines in the file.  Delete all the "The IP" stuff.

"auto lo" should be on a line by itself.  The extra stuff seems odd for a loopback.
Why not have 
"auto eth0" line?

network and broadcast are useless. Remove them.
I can't recall when, but DNS settings have to go into the interfaces file  - think that started in 14.04, but I don't remember.

BTW, in 16.04, networking changes again and in 17.10, yet again.  People trying to make things that have worked for 20 yrs, "better."  They are solving issues I never had.  Anyway, be prepared for those new things up front.

If you delay moving to new LTS releases, people who may reply don't recall things as clearly as we do within the first year.  Most of my servers are still on 14.04, BTW.

---

### Post by patdundee on 2018-01-01
Hi 
It seems iproute2 had not been installed is there a way this package can be obtained and installed via a usb stick

---

### Post by TheFu on 2018-01-01
Did you make the suggested changes or not?

---

### Post by patdundee on 2018-01-01
I did but it made no difference. All my 14.04 servers are set the same way and all work fine :)

---

### Post by TheFu on 2018-01-01
> **patdundee said:**
> I did but it made no difference. All my 14.04 servers are set the same way and all work fine :)

Good to know.

ifup/ifdown aren't needed if the 'auto eth0' is included.

Or

You can use *ifconfig ... up* if you like, provided the device is known as eth0.  With 16.04, all device names changed thanks to systemd fixing a problem I wasn't having.  The new device names are based on the MAC, so pseudo-unique.  This will help when you get to the 16.04 parts.

You can pull the iproute2 deb from any of your other, working, servers if they are from the same release and install that.  Be certain to immediately update it post-working-network, so any updates are part of your normal weekly patching.

---

