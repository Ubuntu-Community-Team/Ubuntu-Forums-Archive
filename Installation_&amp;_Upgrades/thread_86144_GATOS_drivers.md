---
title: "GATOS drivers"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by drashkeev on 2005-11-04
Hi,

I'm thinking of installing ubuntu on a computer that we built to use as a television, out of parts that we had laying around and/or got at garage sales. The crown jewel of this baby is an ATI all-in-wonder 7500 that we got from an old computer. For some reason, we couldn't get windows to recognize the card at all, and finally ended up installing knoppix, with the binary drivers from gatos.

For those not in the know, gatos, from gatos.sf.net, is a system of drivers that aims to provide support for ATI TV-in (I don't need capture or TV-out). It comes as a source-only driver that needs a compiled X tree in order to compile, which means that every binary one makes is unique to one's particular X tree, and barfs when there is an X version mismatch.

The interesting bit is this: I really don't want to compile Xorg personally, since this computer, while decent, is somewhat low on hard disk space, and it'd be nice not to have your drivers break every time one gets a security update.

The gatos project provides a binary version of their drivers for Xorg 6.7.0 (which doesn't work with 6.8.2, included in breezy), and a binary version for Xfree86 4.3.0, which is included in universe. No debian packages for 6.7.0 exist (as far as I can tell), and no amount of googling has turned up any gatos binary drivers for 6.8.2. Thus, I stayed with knoppix which uses Xfree. The trouble is that I can't upgrade knoppix without either breaking the drivers or breaking something else.

I've been struggling to keep knoppix from upgrading to Xorg, but the only thing that seems to work is to stop using apt, which annoys my sensibilities. Question: under breezy, has anyone had any success keeping X down to Xfree86 4.3, or at least running both Xorg and XFree86 together? Do those packages in universe actually work? Will it break anything if I do a minimal install, pin the packages to 4.3.0, and then apt-get install gnome?

Yours truly,

--Dmitry

---

