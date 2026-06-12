---
title: "Loss of Network Functionality Following Upgrade to Feisty"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by kwn12 on 2007-04-27
After upgrading to Feisty using the "official method," I am left without internet access. I do not use a router, the cable modem is directly connected to a PCI ethernet card. Interestingly, I had a nearly identical problem after upgrading to edgy. A complete reinstall was my eventual solution to the problem. What follow are a few peices of information that may be of interest. 

lspci provides the following information on (what I assume to be) the ethernet card:
*"02:0b.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)"*

The NetworkManager Applet, found at the top-right of my desktop, has an "error" sign over it. When the cursor lingers over the icon, a popup announces that there is "no network connection." Right-clicking presents the option to "Enable Networking," although it doesn't seem to do anything when clicked. 

The Network Settings configuration shows a "Wired connection" configured for dhcp.

Thanks in advance for any help!

---

### Post by kwn12 on 2007-04-27
Ok. I seem to have at least temporarily fixed the issue by messing around with ifup and the like. The card (eth0) was for some reason showing up sporadically in ifconfig. NetworkManager still seems clueless, but that will probably be resolved after a reboot.

---

### Post by Red Knuckles on 2007-04-29
This worked for me in Linux Mint Bianca KDE. The KNetworkManager icon still pops up though I'd like to figure out how to stop that. Or I'll just hide it in system tray. Here's the instructions:

Disabling network manager in your gnome session will not work as that is just the 'notification area' for the network-manager service. To disable network-manager, either uninstall it (which will break ubuntu-desktop package) or do this:

Stop network manager...

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

Reboot.

I know he's talking about Gnome but it worked for me in KDE. :guitar:

---

