---
title: "Problem with DHCP when install using Ubuntu minimal CD iso"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by Mandalord on 2015-05-18
Hi guys,

I tried to make a clean, non-bloated install of ubuntu on a Virtualbox VM using Ubuntu minimal CD iso of ubuntu 14.04.

The VM is pretty simple: Xubuntu 14.04 as host-OS; all specifications of VM is default, except 2 network devices: eth0 is bridged, etho1 is internal.

The iso booted fine with the VM. I chose the expert install option to be able to control every step of installation.

The installer starting fine, then it get stuck with 1 point: it cannot connect to the DHCP server and gateway.

My network was at school, gateway ip 10.3.7.1, ip range 10.3.7.0/24, using DHCP. All my other device were working fine. Another VM using normal Ubuntu iso connect fine.

After some tries, only this worked: After detecting network hardware, I ran the shell and added file /etc/modprobe.d/blacklist, the file contains "blacklist ipv6". Then I exit the shell and back to configuring dhcp, press Enter quick to cancel IPv6 configuration. Then DHCP auto configuration worked like a miracle.

It seems the problem lied with IPv6, since my network use IPv4. There is no option or way to configure DHCP to work with IPv4 except the way above. If I did anything above wrong, even in order of thing, DHCP auto-configure would not work correctly.

I'm not a very good Linux user, just an amateur with some experience. I don't even understand much of what I did, just thinking adding the line "blacklist ipv6" could prevent loading IPv6 module, or something like that.

Can anyone explain to me what happened? Is there any way to force using IPv4 during install? Should developer add ability to detect IPv4 during text-based install?

Thank you!

---

### Post by sudodus on 2015-05-22
Welcome to the Ubuntu Forums :-)

There is a difference in the network configuration between the mini.iso and normal Ubuntu (I guess you mean Ubuntu desktop (with Unity)). Normal Ubuntu uses a more automatic approach. You can use the following link to make the network by the mini.iso more automatic,

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Unmanaged_Wired_Network)

---

