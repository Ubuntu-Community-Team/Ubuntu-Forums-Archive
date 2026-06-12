---
title: "Installation tarballs? (Gentoo style)"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by tbaac on 2007-08-17
Following its appearance on a Linux Format coverdisk I decided to try Gentoo 2007.0
My laptop is an AMD64 and as that version wasn't on the coverdisk, I installed from the command line instead by booting the Kubuntu Edgy AMD64 Live CD that I had and then downloading the Gentoo tarball, extracting it to the hard drive, chrooting to the new environment and finishing off the installation.
I finally gave up on Gentoo for the moment (because there seemed to be a bug in the Realtek NIC driver for the latest kernel that prevented it from compiling).
I then came back to Kubuntu, installed Edgy from the previously mentioned Live Cd and then upgraded to Fiesty then Gutsy.
However, the ability to install Gentoo from a Kubuntu live cd really impressed my small little mind.  My question is, can you do the same with Kubuntu?  (stick the live cd into the drive, boot up, download a tarball and then install from the live environment)
Or is that a silly question?

Thanks.

---

### Post by Bachstelze on 2007-08-17
[https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

The page says Knoppix but it works from any Live CD.

---

### Post by tbaac on 2007-08-18
> **HymnToLife said:**
> [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)

The page says Knoppix but it works from any Live CD.

Nice one, thanks HymnToLife.
I was looking at Debootstrap last night actually (because I want to run Defcon on my AMD64 and it only seems to work on 32 bit hence using Debootstrap).
Its good because I'm moving house at the moment and my wife's packed all the blank CDs, so its good to know that I can reinstall that way if I want without upgrading Edgy which is a pain on a new install (like doing the installation 3 times).

Cheers.

p.s.  Isn't Gutsy great?  (apart from the name obviously)
Only trouble I've had so far was when I tried installing the 32 bit version of libxdamage to try to get Defcon to work.  Defcon did work but nothing else did (even Synaptic) as they all had the 64 bit version as a dependency.  "dpkg -r" the 32 bit library, apt-got the 64 bit version and everything was okay again.  I know not to do that again now.
Anyway, I waffle, thanks for the advice, cheers.

---

