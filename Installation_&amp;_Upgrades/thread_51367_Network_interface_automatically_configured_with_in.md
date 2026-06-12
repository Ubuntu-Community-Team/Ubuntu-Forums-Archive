---
title: "Network interface automatically configured with invalid MTU (0)"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by pauldoo on 2005-07-23
Hi,
I've just installed Ubuntu 5.04 (amd64) and the install went pretty much perfectly apart from the network configuration.

I have an onboard nForce4 nic and when booting it configures the interface on DHCP (apparently successfully) but sets the MTU size to 0, making the interface totally useless.  I need to manually run "ifconfig eth0 mtu 1500" before I can begin using it.

Is there an easy way to tweak perhaps /etc/network/interfaces to use DHCP but have a manually set MTU?  The man page suggests that the option for setting the MTU is only available in the static (non DHCP) setup.

---

### Post by kleeman on 2005-07-23
In /etc/network/interfaces use the following lines:

auto eth0
iface eth0 inet dhcp
up ifconfig eth0 mtu 1500

works perfectly for me.....

---

### Post by pauldoo on 2005-07-23
Interesting, perhaps I got the wrong end of the stick from the man page but I'm sure it said that manual mtu settings can only be used if the interface is configured as 'static' and not 'dhcp'.

I'll give this a shot tomorrow when I'm back at the machine in question.

---

### Post by pauldoo on 2005-07-24
[QUOTE=kleeman]In /etc/network/interfaces use the following lines:

auto eth0
iface eth0 inet dhcp
up ifconfig eth0 mtu 1500

works perfectly for me.....[/QUOTE]
 Unfortunately this hasn't worked for me.  Perhaps your default MTU is already ok and manually setting it is redundant.  On my system at least the line you suggest adding has no effect.

It's no big deal having to hack an extra init script to run what I currently run manually at bootup.  I just thought I should raise the matter.

---

### Post by kleeman on 2005-07-24
Hmmm. On my system the default mtu was 1486 and this line does raise it to 1500 (I checked with ifconfig). What is strange is that all the command 
up ifconfig eth0 mtu 1500

does is to execute ifconfig eth0 mtu 1500 following the bringing of the interface up. Something must be resetting your mtu to 0 after this.

---

