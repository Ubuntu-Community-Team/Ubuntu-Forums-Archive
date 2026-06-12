---
title: "Ubuntu on an older server motherboard (aka 2 CPUs)"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Aishiko on 2007-08-16
Hello all I'm going to be doing yet another attempt at Linux, this time Ubuntu is the flavor I'm trying.  In the past It's not been harder to get working then I've had free time.  Usually my issue has to do with mounting drives, and getting media files to work as well as networking.

I'm savy enough to get put a computer together on the hardware level, now I'm curious to know if anyone has installed on or knows of any issues of installing on the following config.

Tryan Tiger (100 or 133)
2 P3 700Mhzs (yes I can't afford to upgrade to an AMD series CPU)
ATI 7200 series or Nivida GeForce 5500 or Nividia MMX series
Creative Labs soundcard model CT4750 or Sound blaster 5.1/or 6.1
1 gig of reg ECC RAM PC100
I beleive the DVD drive is a Toshiba OEM
and a PPA int'l 5 port USB 2.0 PCI expantion card
and a WD Hard drive 4 to 70 gig hard drive

I've built mine out of spare parts that I've gotten from friends, off ebay, or salvaged from computers being thrown away by businesses that I was friends with the owner, and the biggest score of parts came when my community college moved from an old building to a new building and threw away several out dated computers and let those of us students that were helping move the stuff that was being saved and moved between the 5 or 6 of us that came in and helped over the course of 3 days/weekend, ohh and I bought a few parts new.

---

### Post by ddrichardson on 2007-08-16
You shoud be OK, providing you use a SMP kernel. There are some issues with GeForce 4 MX cards, but they are workable.

---

### Post by Aishiko on 2007-08-16
SMP kernel? is that the standard Unbutu 6.x kernel or the 7.x kernel?  Or does it require me to do more then use the standard iso download to use in a standard PC config not a server config?

---

### Post by ddrichardson on 2007-08-16
It should be configured during install. If not it can be through Synaptic.

---

### Post by Aishiko on 2007-08-16
Synaptic?  I can't seem to find a thread that talks about how that is used or what it is it is always a refrence to that program.  Is it intergated or is it something I'll have to go out and download and install?

---

### Post by lloyd_b on 2007-08-17
> **Aishiko said:**
> Synaptic?  I can't seem to find a thread that talks about how that is used or what it is it is always a refrence to that program.  Is it intergated or is it something I'll have to go out and download and install?

Synaptic is a GUI package manager, and it's installed by default on Ubuntu/Xubuntu installations (I believe Kubuntu uses "Adept" instead).  It allows you to select and install various packages (of which the kernel is one).

Ideally, the installer should detect the multiple processors, and install the appropriate SMP kernel.  If not, then still no problem - it'll just be running on one processor until you install the SMP kernel.  Intel multi-processor machines boot by default using only one processor - it's up to the OS to enable and use the other processor(s).

Lloyd B.

---

### Post by Aishiko on 2007-08-17
thank you  Lloyd and richardson  You've both been most helpful.  I think I'll try a dualboot system with XP Pro first.  Though I can't remeber if Both OSes have to be on the same physical harddrive or if I can have one on 1 hard drive and another on a second.  I'll have to look up the right way to do that. :)

---

