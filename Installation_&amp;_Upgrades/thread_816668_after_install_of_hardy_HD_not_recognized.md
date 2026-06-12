---
title: "after install of hardy HD not recognized"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Prince_Dor on 2008-06-02
First the computer specs.

MSI MS-16332 Laptop
Chipset Nvidia C51M + MCP51M
video card: Nvidia GeForce Go 7600 256meg
Ram 1gig
Processor AMD Turion 64x2 tl-52
Both wireless and wired ethernet.
80GB HD
other stuff I can post if needed.

Laptop installed and ran 7.10 fine. 
Tried to upgrade to 8.04 beta. Install went fine. rebooted, the compter ran the post test. then hangs without trying to boot.
rebooted with the live cd same problem.

Sent the computer in for service they replaced the motherboard. Blamed it on a bad Sata controller chip.

got the computer back with Vista on it. 
waited for 8.04 final to come out, tried to install 8.04 again same problem, this time I had a backup hard drive with my Vista install on it. Put it back in the drive boots up fine.

Put the sata drive in another computer and it boots fine in that computer, but will not boot in the laptop ?

I'm thinking problem with the install on this chipset any ideas what to try.

Thanks

Prince Dor

---

### Post by cmnorton on 2008-06-04
Have you tried a text-mode only install?

Have you tried a command line system install; gotten network connectivity; and then installed your Gnome or KDE desktop?

The first two questions point to graphics. My Thinkpad T61p works just fine with 7.10; did install 8.04; and in both cases I had to get around the nvidia chipset. For the Thinkpad T61p, I chose the vesa driver, because the Thinkpad plays in a KVM enviornment with an Acer AL1914 monitor.

An older Acer Travelmate 630 (also Nvidia graphics) installed 7.10 fine, and neither 8.04 XUbuntu or KUbuntu would install on it, and the description sounds like yours. 

Can you boot this system with Knoppix, my favorite diag tool?  (Note, make sure you blast the latest Knoppix CD; it made a difference with a Thinkpad T61p.) 

Booting with Knoppix gives you a benchmark; there is nothing magical in this step.

---

### Post by Prince_Dor on 2008-06-04
no haven't tried text only. I will do that and let you know how it turns out. 

What I'm bothered by is that I don't get to see even the grub loading messages and once I do the install I am unable to boot even off the cd with the hard drive in. Once I take the HD out it starts to boot again. 

Thanks again for the thoughts on text only.

Greg (Prince Dor)

---

### Post by revvol on 2008-06-16
I have the same problem.  Install works fine for 7.10, 8.04 and OpenSuse 10.3

But as soon as I reboot, nothing.  It won't even boot from cd, until I remove the hard drive.  I have to delete the linux partitions in order to reinstall.

I've tried text only, and command line only versions of Ubuntu 7.10 with no luck.  Same issue.

I've read about people using linux on this laptop...  but how?

---

