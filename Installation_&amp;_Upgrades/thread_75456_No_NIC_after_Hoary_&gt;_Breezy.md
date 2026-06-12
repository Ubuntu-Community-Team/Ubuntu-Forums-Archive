---
title: "No NIC after Hoary &gt; Breezy"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Finchwizard on 2005-10-13
Just upgraded my personal server up.

Everything went fine, apart from I have no network card now, I'm not hugely great a linux, but know a few things.

*lsmod* has loaded the right module, which is e100, it's a Intel Ethernet Pro card, 100MB

The settings are still correct in */etc/networking/interfaces*

But when I do a *ifconfig*, I only see the loopback.

Any suggestions, worked fine before the upgrade, now it doesn't seem to work =(

---

### Post by HermanAB on 2005-10-13
Have you tried 'service network restart'?

---

### Post by Finchwizard on 2005-10-13
Says 'service' command can't be found.

But I did try /etc/init.d/networking restart with no luck.

I also tried running Hotplug again, no luck.

---

### Post by badarras on 2005-10-13
The same happened to me after my upgrade.  I no longer have network access.

---

### Post by Finchwizard on 2005-10-13
At least I'm not alone, I can't even get it back.

I managed to assign an IP address to the network card, after 'ifconfig eth0 up'

Then setting it manually, I got a few host lookup things, whatever that's on about.

But now it's all gone and I'm back where it started to, I can't believe it upgraded all these packages, Apache, MySQL, Postfix, you name it, but blew apart my network card.

Any other ideas? I'd really like to get it back up and running.

**Edit**

After making a simple hosts file with my IP to the computer name.

Moving /etc/networking/interfaces to a backup, and recreating with the following settings.

> 

auto lo
iface lo inet loopback

mapping hotplug
script grep
map eth0

iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
network x.x.x.x
broadcast x.x.x.x
dns-nameservers x.x.x.x

auto eth0


After doing that and recreating it (Which was exactly the same as the other one keep in mind) and restarting network services worked.

At least I'm up and running, enough time for me to get data and move back to a Debian server, Ubuntu was running so well before this breezy update, to blow apart something as simple as a NIC is pretty rough.

---

