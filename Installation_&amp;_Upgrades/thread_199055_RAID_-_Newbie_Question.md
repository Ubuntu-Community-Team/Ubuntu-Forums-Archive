---
title: "RAID - Newbie Question"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by blazer666 on 2006-06-18
Hi I have just booted off the Ubuntu dvd and the desktop has loaded, I select the install icon and It asks me which disk I want to install it on I.

I have a raid setup on a LANPARTY UT nF4 SLI-DR motherboard and 2x WD Raptor drives. I want to install on the raid array and not on a single disk.

I went to the DFI website and there is a Linux driver, inside the driver archive are drivers for redhat and suse linux.

Firstly where is the option to install ubuntu on a raid drive? and secondly where can I get drivers for my raid controller I am using the NVIDA raid controller ATT the board has 2 seperate RAID controllers NVIDA and Silicon Image Sil 3114?

---

### Post by wombat20 on 2006-06-18
First, work out if you have real RAID or fakeRAID.  If it's part of the mobo it's likely to be a fakeRAID which needs a driver to work with any OS.  If you try to install Ubuntu onto fakeRAID it sees it as two HDs.  From what I've read it's better to install the software RAID which comes with Ubuntu.  Have a read of this:

[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)
and this...
[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

If you're trying to dual boot on a single RAID array, that's a whole different story...

---

### Post by blazer666 on 2006-06-18
Thanks for that will have a read, although its a bit confusing for a window user!

---

