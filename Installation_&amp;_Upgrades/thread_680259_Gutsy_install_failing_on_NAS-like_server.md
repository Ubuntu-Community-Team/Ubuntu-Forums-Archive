---
title: "Gutsy install failing on NAS-like server"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by PRMan on 2008-01-27
My wife's parents gave me an old computer where the drive crashed but everything else about it seems fine.  It's an old Soyo P41 Fire Dragon motherboard with a Pentium 4 1.8 in it.  I figure it will run about 80 watts while idling, which is pretty good for a 24/7 box.

I am trying to setup a 4-drive NAS box to store all our documents, pictures, etc. from a bunch of Windows clients.  Also, I would like to install fuppes (or some other upnp server) to serve the content to a DirecTV HR20 DVR.

I am tired of dealing with Microsoft's upgrade nonsense on my 2003 Server, where they shut it down and reboot it sometimes even though I have Automatic Upgrades set to DOWNLOAD ONLY!!!  But apparently they don't respect my wishes! :(

So, I would like the NAS to run Gutsy.  I install the live CD and it works fine, but after installing the computer goes into an endless reboot loop.  It will run boot CDs just fine and I was able to upgrade the BIOS to the latest version, which turns on support for drives over 137GB.

I'm not using the Server install, because, as a Windows and Windows Server user for many years, I like having the desktop in place in case I need to go on there.  I'm not good enough at the Linux command line to be without it for a lot of things (hardware information, etc.).

I realize I could install the Server CD and apt-get the desktop later.  Might that help me debug why the install process is failing?

Where should I go from here (other than installing Windows XP Professional and Windows Media Player 11)?

Any ideas?

---

### Post by PRMan on 2008-01-27
Oh, yeah, I have verified the CD using the tool on the Boot CD itself, so it's burned correctly.

---

### Post by PRMan on 2008-01-27
At second glance, I think it may be related to the Intel 1000 MT card trying to network boot.

I'm going to try a Netgear GA311 card I have laying around instead.

---

### Post by PRMan on 2008-01-27
Nope, same problem.  Maybe the motherboard isn't good after all...

Has anyone seen a situation like this?

If I boot from the Live CD, I can see all the drives and work for hours with no problems.

---

