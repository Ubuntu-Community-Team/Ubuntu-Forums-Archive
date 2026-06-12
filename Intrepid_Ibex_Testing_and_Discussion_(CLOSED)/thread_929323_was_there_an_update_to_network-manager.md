---
title: "was there an update to network-manager?"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Neon Lights on 2008-09-24
I just updated, restarted, and now I have no internet. It's a wired connection to my router, and it won't connect. /:
halp?

---

### Post by alphacrucis2 on 2008-09-24
> **Neon Lights said:**
> I just updated, restarted, and now I have no internet. It's a wired connection to my router, and it won't connect. /:
halp?

It is still working for me but I am using a static IP (although that didn't work with earlier versions). Maybe it is now having trouble with DHCP?). I have been having trouble getting it to retain a second static address. For me NM has been the worst thing in this release

---

### Post by Foaming Draught on 2008-09-24
Have you **left**-clicked the NM icon in your taskbar, and re-checked *Auto eth0*?  It unchecked itself on my system last night.

---

### Post by Neon Lights on 2008-09-24
Yeah, it has been a pain. I've never had problems with my connection personally though...I mean, none that a restart didn't fix. xD But uh, so how would I go about switching to a static IP? I mean, I can right? ._. I don't believe I have a dynamic one. I don't know. >.< hahaha

EDIT: and no, it doesn't give that option. It says no network devices available. /:

---

### Post by NickelGuy on 2008-09-24
Yup, having the same problem here.

---

### Post by NickelGuy on 2008-09-24
> **Neon Lights said:**
> Yeah, it has been a pain. I've never had problems with my connection personally though...I mean, none that a restart didn't fix. xD But uh, so how would I go about switching to a static IP? I mean, I can right? ._. I don't believe I have a dynamic one. I don't know. >.< hahaha

EDIT: and no, it doesn't give that option. It says no network devices available. /:

You may want to check what ethernet driver ibex is using.  It seems the e1000 driver is kaput for now. Check out the following post for more info...

[http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

---

### Post by Neon Lights on 2008-09-25
When I try ifconfig, it only shows "lo", no eth0 or eth1 /:
hence, ethtool simply says it cannot get the driver info, because there is "No such device".

---

### Post by john_navarro on 2008-09-25
Same problem happened to me after an upgrade - but I don't have an e1000 card:

lspci:

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

$ ethtool -i eth0
driver: tg3
version: 3.86
firmware-version: 5755m-v3.29
bus-info: 0000:09:00.0


Oh, got this info from a Hardy install on a different partition.

---

### Post by ShirishAg75 on 2008-09-25
Have to go for a reboot, scared a bit as NM has got upgraded. While other things can be fixed, if you do not have network that kinda puts spoke in things. 

Here's my info, in case if it doesn't work out then will ask for help from a cybercafe ;)

```

$ ethtool -i eth0
driver: 8139too
version: 0.9.28
firmware-version: 
bus-info: 0000:03:02.0

```

```

$ lspci | grep Realtek
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

---

### Post by Neon Lights on 2008-09-25
Okay, so I booted up a Hardy livecd, anddd...my driver is e1000.
I'm rather lost with the situation. /: forgive me, I can be slow haha, but is there anyway I'm gonna be able to run intrepid? I mean, before they figure out whats wrong? I thought it was a problem with a specific card.

---

### Post by Jack M. on 2008-09-25
Try rolling back to the 2.6.27-3 kernel (sudo gedit /boot/grub/menu.lst and change all the '-3' to '-4'). I'm not sure what changes they made in -4, but it broke my network also and rolling back fixed it.

EDIT: Didn't see that part. The above is probably really bad advice then.

---

### Post by Scruffynerf on 2008-09-25
There is a sticky at the top of this forum that you really should read.

Essentially what is happening is that somewhere (current thinking seems to be something in Xorg 7.4) that dies, and writes garbage over the firmware.

So, as a protective measure, there was an update to NM that disables wired ethernet on some systems, as a protective measure to prevent your wired ethernet controller becoming as useful as a stone.

IE: The bug is currently *permanently* breaking hardware. As in: return to manufacturer. Even if you dualboot, and go into windows, your hardware is likely to still be toast if the bug bites.

---

### Post by Neon Lights on 2008-09-25
> **Scruffynerf said:**
> There is a sticky at the top of this forum that you really should read.

Essentially what is happening is that somewhere (current thinking seems to be something in Xorg 7.4) that dies, and writes garbage over the firmware.

So, as a protective measure, there was an update to NM that disables wired ethernet on some systems, as a protective measure to prevent your wired ethernet controller becoming as useful as a stone.

IE: The bug is currently *permanently* breaking hardware. As in: return to manufacturer. Even if you dualboot, and go into windows, your hardware is likely to still be toast if the bug bites.
Okay, thank you for clearing that up. I did read the thread, I just didn't quite get it all. xD

Alright, SOO, until they figure that out, I have to stick with an earlier version of ubuntu? And is Arch Linux affected? ._. I have that as my other OS, and yeah.... xD

Edit: Uhm, wait, upon rereading, it says only e1000e cards were affected, and that e1000 users weren't. How come mine was blacklisted?

---

### Post by Scruffynerf on 2008-09-26
@Neon:

It isn't just Ubuntu. The linux kernel testers are working on it, and a couple of them have lost hardware owing to the bug. It's present in either the linux kernel itself, in the .27-rcx versions, or in Xorg 7.4. So far the bugs have been reported in:
Ubuntu
RedHat
SuSe
Gentoo etc. So far, about the only major distro chain not affected is Debian itself.

Arch is likely affected if it is using the above kernel and/or xorg version. Keep in mind as their userbase is smaller, there is a smaller number of people potentially affected by the bug.

Answering your question specifically, you card might be reliant, or dependent on either e1000e or e1000 (the 2 blacklisted modules), hence why it is not working.

What version of ubuntu you decide to use is up to you. Keep in mind though, that there is a known serious bug with the bleeding edge code at the moment, which may damage your hardware.

Edit: A summary of the issue currently appears at [http://lkml.org/lkml/2008/9/25/510](http://lkml.org/lkml/2008/9/25/510)

---

