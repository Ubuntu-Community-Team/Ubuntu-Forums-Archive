---
title: "trying Ubuntu 13.04 from live DVD, no networking"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2013-09-18
Want to get Ubuntu 13.04 running on a new desktop.  It has Windows 8 installed already.  When running Windows, network connection is perfect.  But when I boot to the live DVD (burned from the downloaded iso) and "try Ubuntu without installing" I can't connect to the network, so there is no internet during the install process.

Any ideas how to fix this?

---

### Post by carl4926 on 2013-09-19
Are you meaning wired or wireless?

---

### Post by raymondvillain on 2013-09-19
Wired.  Ethernet works with Windows 8 just fine, no issues.  Ubuntu won't connect, for some reason.

---

### Post by raymondvillain on 2013-09-19
Realtek PCIeGBE Family Controller

---

### Post by carl4926 on 2013-09-19
Are your windows 8 is properly powered off?
They made a dogs breakfast out of that @microsoft

---

### Post by raymondvillain on 2013-09-20
It happens even if i disconnect the drive on which Windows 8 is installed.  Tried a different router, still no network.  Baffling.

---

### Post by raymondvillain on 2013-09-20
This is a machine I built myself, are there issues with Gigabyte motherboards?  Is there a setting I can change in BIOS?  If I install 13.04 without a network connection, will I be able to set up one after the installation?  Is this worth a try?

---

### Post by carl4926 on 2013-09-20
If it's a BOX, slap a PCI network card in it
They are cheap as chips
D-Link ones are easy to find on auction sites

---

### Post by raymondvillain on 2013-09-20
I did just that, a Trendnet card.  Network cable has been moved from the on-board network connection to the new one.  Windows 8 works fine, but not Ubuntu.  When I'm running the live CD, I opened a terminal window, typed lspci -v and got 2 blocks of text with ethernet info, both list "kernel driver in use: r8169" which makes me think that the ethernet controller built into the motherboard and the trendnet card I installed use the realtek hardware, and perhaps Ubuntu doesn't like the realtek driver.  Will look for a different network card tomorrow, stores all closed here now.  Thanks for the suggestion.  If I'm right, how will I get Ubuntu to use the PCI card and not the controller built into the motherboard?

---

### Post by raymondvillain on 2013-09-20
What Gigabit ethernet cards are folks using with Ubuntu?  My motherboard has a Realtek built in, 13.04 doesn't work with it.  I put a trendnet card in but it uses hardware that ubuntu thinks needs the realtek driver, so no luck there.  Is an intel gigabet ethernet card a good choice?  Need to avoid using the realtek 8169 driver.  The hardware compatibility list seems out of date to me.

---

### Post by carl4926 on 2013-09-21
```
Network:   Card: Realtek RTL8111/8168 PCI Express Gigabit Ethernet controller driver: r8169 
           IF: eth0 state: up speed: 100 Mbps duplex: full
```

That is mine
Works fine

---

### Post by raymondvillain on 2013-09-21
Solved.  It was the realtek ethernet driver.  I put an Intel ethernet card and everything works.

---

