---
title: "reinstall network manager without Internet"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by davidsanchezvasquez on 2010-02-15
I have been trying to do this without success

Today I was trying to configure a wireless network for my pc and it ended in a mess and now I dont see anywhere the wifi icon (yes, I have already tried "add notifications") 

The thing is that it seems the whole network manager is not longer there

I have downloaded the package to reinstall it (Im writing now from a friend's pc) without sucess, because network manager needs other packages who are supossed to be downloaded from the internet while the installation, but I do not have Internet!

So what can I do?

Any help will be appreciated

---

### Post by adam814 on 2010-02-15
Basically you have two options.  Strictly speaking you don't absolutely need NetworkManager for an internet connection, so you can configure your connection manually on the command line (can be a pain if you need to connect to a WPA-protected wifi network, not difficult at all for wired connections).

For a wired connection most likely all you need to do is connect the cable and run this in a terminal:
```
sudo dhclient eth0
```Of course that's assuming your ethernet interface is eth0 (could be eth1 if you have 2 NICs).

Or since you're able to post here I imagine you have another machine with internet access or at least a LiveCD.  From that environment you can download the .debs you need from packages.ubuntu.com.  Here's the ones related to network-manager I have on mine:
```
network-manager
network-manager-gnome
network-manager-openvpn
network-manager-pptp
network-manager-vpnc
```
I think the last ones can be left out depending on your particular VPN connection needs.

---

### Post by davidsanchezvasquez on 2010-02-15
thank you, the problem is solved :D

I re-installed the following packages in that order:

1) modemmanager
2) network-manager
3) network-manager-genome

Then re-started the system and I have my Wifi icon back and thus Internet again :)

Cheers!

---

