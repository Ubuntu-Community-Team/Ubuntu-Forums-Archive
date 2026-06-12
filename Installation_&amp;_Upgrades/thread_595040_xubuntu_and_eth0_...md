---
title: "xubuntu and eth0 .."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by emacsuser on 2007-10-28
I installed Ubuntu on a dualboot desktop with two NICs, one static one DHCP. on boot repeatidly kept losing the cards. Multiple use of ifdown/ifup sometimes brought them back up. I changed to Xubuntu and now no network access at all. Don't have these problems with Windows on the same machine. Any solutions please ...

ETH1 Realtek RTL8139 Family
ETH0 SiS 900-Based PCI Fast Ethernet Adapter

---

### Post by ofb on 2007-10-29
I haven't solved this one so take this as anecdotal.

I've run installs of 7.10 Kubuntu, Ubuntu, Edubuntu, and Xubuntu on my test box with two NICs. Always networks problems. I eventually found the thing to do was uninstall that 'roaming' network-manager and set DHCP and static manually through System > Admin > Network.

That said, my main box also has two NICs. I had it set manually, with the Network Manager applet disabled in startup apps (System > Prefs > Session) back around 6.10 or 7.04. I have just done a fresh install of 7.10, although keeping my old /home partition. So that applet is still disabled, but I note the cards are both set to Roaming, and I see I have network-manager listed as installed in Synaptic.

My DHCP eth0 has been working just fine. I haven't tested the LAN yet.

---

### Post by julian67 on 2007-10-29
I run Xubuntu 7.04 on my desktop with 2 network interfaces, one being the ethernet port built into the motherboard and the other is a USB wi-fi dongle. The USB wi-fi adapter (Safecom with Zydas chip) is internet facing and uses DHCP and WPA encryption.  The wired adapter (SiS 900-Based PCI Fast Ethernet Adapter ) is LAN facing and uses static IP address. I found the best/easiest/quickest way to do this was by installing network-manager-gnome and nm-applet and doing all the config via the nm-applet. 

If you want to start over with network-manager make sure /etc/network/interfaces looks like this and has nothing added after iface lo inet loopback

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

I notice you use Realtek RTL8139 Family. I have this same adapter on another PC (laptop) which is dual booted and recently had some seemingly bizarre problems. It turned out that the culprit was an updated driver delivered via Windows Update. This driver changed the adapter's config so that the "wake on LAN after Shutdown" ability was disabled. This is important because the Linux drivers aren't able to properly start the card if this is done. I suggest you boot into Windows, go into the System Properties (<Winkey><PauseBreak>) >Hardware>Device Manager>Network adapters. Right click the realtek card>Properties>Advanced and change the "Wake-On-Lan After Shutdown" Value to "Enabled" and OK it.  I hope that when you boot back into Xubuntu you have your Realtek card up again.

---

### Post by emacsuser on 2007-11-07
I transplanted the harddrives to new hardware and it works now. Just had to reconfigure Xorg. Windows gives me a blank screen and won't let me boot in safe mode, so I guess it's time for another reinstall ...

---

