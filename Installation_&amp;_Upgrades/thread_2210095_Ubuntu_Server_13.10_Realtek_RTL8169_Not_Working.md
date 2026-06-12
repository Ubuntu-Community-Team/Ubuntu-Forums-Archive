---
title: "Ubuntu Server 13.10 Realtek RTL8169 Not Working"
date: 2014-03-09
forum: Installation &amp; Upgrades
---

### Post by mastermindg on 2014-03-09
I got a gigabit RTL8169 card thinking that I would have no difficulty with this card in a 13.10 install. Unfortunately I have had nothing but trouble with it. I have a link light and indicators are showing activity but I don't get any IP/dhcp communication from the card. The card is fine and ethtool even shows link up. I just don't have any connectivity. Any ideas?

---

### Post by varunendra on 2014-03-09
Please post the output of ethtool and lshw -
```
sudo lshw -numeric -C network -sanitize
sudo ethtool eth0
```

And check BIOS. If there is an feature called "IOMMU", try changing its state.

Have you done normal sanity check? That is, checking (or replacing if possible) the cable and the contacts?

---

### Post by mastermindg on 2014-03-09
It's difficult to post a full readout as I don't have network access to the box. However:

```
description: Ethernet interface
product: RT8169 PCI Gigabit Ethernet Controller [10ec-8169]
physical id: 6
bus info: ....
logical name: eth0
version: 1A
...
...
....
capabilities: pm bus_master cap_list rom ethernet physical
configuration: autonegotiate=on broadcast=yes driver=r8169 driver version=2.3LBK-MAP....
resources: irq:20....

```


Snippet of ethtool:

```
Speed:1000MB/s
Duplex: Full
Tranceiver: Internal
auto-negotiation:on
current message level: 0x000000022 (51)
drop probe if down ifup
```

I've verified the cable and connection by plugging it into another machine. That machine is recognized instantly. 

FYI: IOMMU is disabled in the BIOS

---

### Post by varunendra on 2014-03-09
> **mastermindg said:**
> FYI: IOMMU is disabled in the BIOS
Gigabyte motherboard? Please enable it > save & exit BIOS > Reboot and check the connection.

Is a snapshot possible? If not, drop the 'Capabilities' parts, but post the full 'Configuration' parts from both lshw (the same line you already posted, but complete) and ethtool (would be multiple lines).

If it is a Gigabyte motherboard, probably enabling IOMMU maybe all you need.

---

### Post by mastermindg on 2014-03-09
Yes, it's a Gigabyte motherboard. I enabled IOMMU and rebooted. It seems to have unrecoverable issues with a previous installation that was done with IOMMU turned off. I'm trying to load the install CD again and see if it can detect my network now.

---

### Post by mastermindg on 2014-03-09
Varunendra... You the man! This is a brand-new PC for me. This is the first I'm hearing about IOMMU but after I enabled it all of my devices are now working fine in Ubuntu. Thanks!

---

### Post by varunendra on 2014-03-09
Awesome! I am as excited as you, because this IOMMU thing is a recent discovery for me too. I came to know of it just a few days ago on IRC from a different IRC user. 
Joys of taking 'Security' to the levels of insanity..:p

Thanks for the feedback! :)

---

### Post by spectatorx on 2014-03-09
Sometimes enabling IOMMU in bios can cause issues (network card recognized and installed but network is not available, sound is not working even if everything seems to be fine, usb 3.0 doesn't work) and if they happen to you add to boot this parameter:
iommu=soft
Personally i wonder why setting it to soft make things to work. To me it happened with motherboard gigabyte ga-990fxa-ud3 rev. 4.0.

---

