---
title: "New install, mostly working, but a couple of teething problems"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by wintermute115 on 2008-10-21
Hi all. I'm setting up a media centre PC, and my first instinct was to build it in XP, but (long story short) it turned into my first Linux install in several years.

I have a 1 TiB Western Digital My Book external drive formatted as NTFS and connected via eSATA (actually, it's plugged into a mobo SATA port via a [passthrough]("http://www.cooldrives.com/intoexes4pop.html")). It connected fine, and I could read and write to it, and I even managed to get it to mount automatically on startup (using UUID rather than /dev/sdxx). But then, for no apparent reason, it started failing; I could navigate through directories on the drive, but creating a new directory failed (I forget the error message, sorry; I had to leave for work). After rebooting, the mobo has no problem seeing it, but Ubuntu can't see it. I run [FONT="Courier New"]sudo fdisk -l[/FONT], and it only lists the partitions on the internal drive. Does anyone know what might have happened, and how I can get it to reconnect?

The other main issue I have is with a wireless network connection. I had bought [a class n card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704031"), when I was expecting this to be an XP project, but the research I've done suggests that that's not going to work under Linux. Can anyone recommend a good class g card that can be set up fairly simply?

Thanks for your time.

---

### Post by Pumalite on 2008-10-21
You could get an USB D-Lynk DWA-110
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

