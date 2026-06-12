---
title: "Dapper to Edgy Eft == broken Network"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by Vevmesteren on 2007-01-26
Good evening all. I upgraded to Edgy Eft yesterday and am having some serious troubles. 

Essentially none of my Network devices work anymore...

When I go to my Networking I see both my wireless (wlan0) and my ethernet card (eth0) as active. 

In my network connection monitor though, only the 'lo' connection is active. My 'wlan0' and 'eth0' do not even show in the dropdown.

I select the Network Tools,  here again the 'lo' is selected by default. My 'wlan0' connection is NOT available in the dropdown. The 'eth0' is. When I select it, there is no ip information available. In the interface information table all items are set to 'not available', the 'interface stastistics' are all at 0....

What this boils down to is...HELP!

can anyone help me?

thanks a lot

---

### Post by Vevmesteren on 2007-01-26
a little update, I have taken a look at my etc network interfaces. And it seems that the names of my interfaces where changed in Edgy. Just updated these (my wireless network used to be eth1 - but to turned to wlan0) in the interfaces with gedit. Rebooted, but to no avail. The icon still stays up there.

Also in the network settings dialog, I just realized that the two network cards that are displayed are BOTH set to beeing Wired connections. Essentially there is something wrong with the Device detection. That is way out of my league. So I REALLY need some pointers here. I would be willing to reinstall I guess, but not loose all my data. Can I install edgy of a CD without having to reformat all my two partitions?

But all that is really not to interesting to be honest, I am sure there is some setup file that I can tweak here. Cause the network cards as such seem to be detected when I access the Device Manager. 

**Wireless card**
Prism 2.5 Wavelan Chipset (the card is detected - but the interface data is unknown)
**WLAN Interface**
Vendor, Device: Unknown
Status: Status
Bus Type: PCI
Device Type: net.80211
Capabilities: net, net.80211

**the wired card**
DP83815 (MacPhyter) Ethernet (the card detects - but the interface is unknown)


HELP!!!!

---

### Post by Vevmesteren on 2007-01-26
iwconfig returns: no wireless extensions on all networkdevices

lo, wlan0, eth0 and sit0

---

### Post by Vevmesteren on 2007-01-26
I have managed to setup my wired card. Remains the wireless one...so really what it boils down to, I realize now, is that wireless Network Cards in general seem to have some serious trouble in Edgy. Does anyone know if there is a fix for that in the pipes. Cause I really do not feel like cabling my entire apartment...

thanks

---

### Post by Vevmesteren on 2007-01-26
well I fixed the problem by the help of a post on this forum.

Something about the driver not working. I am trying to find the post again, but can't here is what I was told to do

switch to Superuser:
[FONT="Courier New"]#sudo -s -H[/FONT]


Edit your blacklist file:
[FONT="Courier New"]#gedit /etc/modprobe.d/blacklist
[/FONT]

Paste the following into the file:
[FONT="Courier New"]#fix the wireless card bug
blacklist prism2
blacklist prism2_pci
blacklist hostap_pci
blacklist hostap[/FONT]

save and close, reboot and I was all set, wireless is back up and running in Edgy

Joy!

V

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

