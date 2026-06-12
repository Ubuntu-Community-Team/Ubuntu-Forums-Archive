---
title: "Installation freezes at file copy"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by starj on 2010-10-08
Greetings. This is my first post so please bear with me. 

I am having difficulty installing Ubuntu on a new PC. Hardware is thus:
MB: ASUS M4N68T-M
CPU AMD Phenom II 3.2 GHz
Mem: Kingston 2GB DDR3-1800
HDD: Seagate Barracuda 80 GB SATA
video is on-board, cannot find the details regarding chipset.

I have tried both 7.10 and 10.10 (would prefer to use 7.10) but both versions hang at the same point during installation.

Live mode works fine on both versions.
Tried burning 7.10 to CD at 4x write speed.
Set MB bios "Plug and Play OS" to yes.

When it hangs, the mouse freezes, then the video wigs out (think Van Gogh on acid) and only a hard power down will un-freeze it.

All help is appreciated.

---

### Post by starj on 2010-11-12
Problem solved! Evidently all three of he optical drives I tried to use to install from CD were, shall we say, less than fully functional. These were drives that I had laying around, supposed working pulls from old machines that I didn't see a reason to toss (got one now!). The fourth drive I used was one we had laying on the shelf at work, in the original box, that had never been installed in a machine. With that drive, everything worked great.

---

### Post by sikander3786 on 2010-11-12
Which one did you install?

> (would prefer to use 7.10)

7.10 has reached end of life and is no longer supported. It would be nearly useless to have that on your system.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Instead try with some live versions i.e, 10.04 or 10.10. All new interfaces, new applications etc.

Regards.

---

### Post by starj on 2010-11-12
Yes, I understand that 7.10 is an older, and I knew going in, most likely no longer supported version. However, this machine is for an addition to a modeling cluster that was built when 7.10 was just released and all of my notes on installation/configuration of the modeling software are based on 7.10. Unfortunately the person who developed the configuration is no longer here and I have been tasked with adding capacity. I admit I am kind of muddling around in the dark a bit. I figured I was safest to start with 7.10, if that wasn't compatible with the new hardware or there were support issues that rendered it un-usable then I would go with the newer version. After getting past the optical drive issue 7.10 installed on the new hardware without issues so I am moving forward with that. 

You do raise another question, though. Part of the required configuration involves making sure certain software packages are installed via synaptic package manager, but when searching for them they do not show up. Is this part of the support you mentioned?

Thanks.

---

### Post by sikander3786 on 2010-11-12
> Is this part of the support you mentioned?

Yes. The repositories are dead for un-supported versions.

---

