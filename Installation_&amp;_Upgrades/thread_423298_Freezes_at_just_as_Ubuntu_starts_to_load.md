---
title: "Freezes at just as Ubuntu starts to load"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by gmtyrant on 2007-04-25
The liveCD runs just fine, and I've had kubuntu installed and working on this machine before, but this time...
I've installed twice, and what happens is during boot, when the ubuntu logo shows and the progress bar is supposed to fill, everything stops. The liveCD still boots fine, Windows XP will boot when I choose it from grub, but Ubuntu freezes.

I'm guessing it's the partitions somehow...tonight when I have access to the computer I plan to try once more, with all new partitions.

By the way, I ran a check on the disc, and it seems to be fine.

If anybody knows what's up, let me know. If I get it to work tonight, I'll post back. Thanks!

---

### Post by johnc4510 on 2007-04-25
Need more info, is Uunbtu already on your hard drive? Or are you trying to install? If it is installed, was this an upgrade or a fresh install?

---

### Post by gmtyrant on 2007-04-25
Hehe, sorry,I've not been concentrating well today.

This is a fresh install of Ubuntu 7.04 on it's very own hard drive, sharing a computer with another hard drive that has XP on it.

As I said before, the liveCD boots up just fine, but after installing, the installed version refuses to load past the black screen with the 'ubuntu' logo and the loading progress bar. The liveCD will still boot, as will my install of XP, so I know it's not a hardware issue.

---

### Post by RAKninja on 2007-04-25
third bar of the loading screen? its a gfx issue i need help with too =\

---

### Post by nuclear_eclipse on 2007-04-25
How long are you waiting before determining it's not booting?  If it is detecting multiple network interfaces, it will try to get a DHCP address on each interface, and for each interface that is not connected to a network, or doesnt exist, it will wait about 30 seconds before timing out on the DHCP request.  Eg, if it shows three devices in your /etc/network/interfaces file and only one is actually connected, that's 60 seconds added to the boot time for the networking modules to wait for DHCP addresses.  

If that's the case, put a '#' symbol in front of each line that declares the disconnected interfaces, and that should eliminate the delays.

---

### Post by gmtyrant on 2007-04-25
It doesn't even load the first bar, RAKninja.

I'm quite sure I waited longer than that, and, though I know it's possible to see the code that's being loaded and such, I don't know what to press to view it.

---

### Post by gmtyrant on 2007-04-25
I've wiped all the partitions and started over, and everything worked fine. I think the problem was from the previous distro I tried to install, Freespire. It had some goofy ideas for partitioning, and I was using the partitions it had laid out.

---

### Post by RAKninja on 2007-04-28
mine is a problem with the integrated graphics chip, the bios, and PCI.  i can get marginal performance out of the pci card, but only when bios is set for integrated control.  none of the fixes listed anywhere have worked.

---

