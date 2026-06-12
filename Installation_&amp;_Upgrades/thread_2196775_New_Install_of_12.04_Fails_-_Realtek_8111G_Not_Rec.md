---
title: "New Install of 12.04 Fails - Realtek 8111G Not Recognized"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by its_your_dad_613 on 2013-12-31
**The Problem:** Attempt to install Ubuntu 12.04 from thumb drive fails because Realteck ethernet controller is not recognized.

**The System:** Brand new Asus H87-Plus main board, i7-4770 quad core, 8 G Ram[B].

Description:[/B] The first attempt to install Ubuntu 12.4 was successful and the Realtek controller appeared to be functioning normally. Next I installed VMware Player 6.01 and installed Windows7 Pro as a guest on my Linux Host. Shortly after completing the VMware install the browser in the virtual machine froze and the connection to my LAN was lost.

**Diagnostics:**

I shut down VMware but could not access the LAN on the Host System. The machine was rebooted several times during my attempts to diagnose the problem and eventually I uninstalled VMware but it make no difference in any settings I checked other than removing the VMnet1 and 8 displayed using "ifconfig".

Using "**lspci**" the Realteck controller was **not** listed

Using "**ifconfig**" the loopback adapter was listed along with VMnet1 and 8 (until they were uninstalled with VMware) but there were no other listings and [B]no listing for eth0.

Also Checked[/B] /etc/network/interfaces and /etc/resolv.conf and /etc/udev/rules.d/70-persistent-net.rules and system BIOS settings.

**Changed Driver** to a version downloaded directly from Realtek as recommended in an Ubuntu forum post.

**Re-Installed Ubuntu 12.04: **During reinstall the Realtek controller did not start and the installer crashed leaving me with an expensive paper weight.

If it's a hardware problem I'll have to go back to the retailer but if there is something else I could try to get the install to work that would be nice. Perhaps I could change the LAN driver used on the install thumb drive.

Suggestion would be welcomed.

---

### Post by its_your_dad_613 on 2014-01-01
**Solution:** I purchased a $10.00 network card (also a Realtek by the way) clicked it into an open slot on my mainboard and connected the new card to my router. I then re-installed Ubunut 12.04 from a thumb drive. All went well and when the install was finished both network cards were listed using the lspci command. Both cards are listed using the ifconfig command.

I don't suggest that you have to reformat your hard drive. I did that because it was a new install on a new machine. The suggestion is that, if you can, pop in a second network card to give you connectivity so you can solve the driver problem of the first card.

Good luck

---

