---
title: "Asus X59SL-F5SL with Mobility Radeon  HD 3470 - Video Problems on Install"
date: 2018-11-30
forum: Installation &amp; Upgrades
---

### Post by lah-ca on 2018-11-30
Hi,

I am working on a lovely Windows-Vista-Era Asus Intel Core2-Duo notebook, preparing it for charity donation.  It is in near-perfect condition, except for a weak battery.

I works well with pretty much any Ubuntu or Unbuntu-based distro up to 16.04, up to but not including 16.04 ***with recent updates***.  The problem is definitely the Ati Mobility Radeon HD 3470 video chipset.

A fresh installation of any 16.04-based distro will work fine, up until all the updates are done.  After the updates, the boot process goes OK, everything normal until after logging in, whereupon there is only a functioning mouse cursor and a black screen.  The best option for a 16.04-based distro seems to be Linux Mint 18.03, Sylvia, simply because its logon screen offers a convenient toggle button between "default" and "software renderingi."  Everything works *well enough *with the software rendering option.

Most 18.04-based distros won't even install.  Some 18.04 distros won't even boot to live media.  The best luck I have had so far is with Xfce distros.  I can get them to install and boot to a log-in screen, but then I am faced with massive video corruption.

I know that the issues here can be resolved *to a degree* at the XServer level by editing config files - there is an overabundance of documentation to this effect.  But this notebook is not for me, nor is it likely for anyone of any technical inclination.  I am looking for a simple, trouble-free solution, one likely to survive future updates, something that will last for a couple of years or more.

The paths of least resistance at this point seem to be Mint 18.03 or Windows 7.  Windows 7 will work just fine (and legally btw), although it does require the use of some Vista drivers to get all the hardware working.  I am reluctant to go down the Windows 7 path, though, because of the monetary costs of owning, maintaining, and protecting a non-FOSS loaded device.  Whoever gets this notebook is not likely to be wealthy at this point in their life.

Any comments or suggestions?

Thx.

---

### Post by lah-ca on 2018-12-01
OK.  This is interesting.  I have now tried a variety of non-Debian, non-Ubuntu-based distros, including some built from scratch - tried with a variety of desktop shells.  For all the current LTS or rolling releases I have tried, the results are the same, exactly the same as with anything built on Ubuntu 16.04 or 18.04.  So whatever the root cause for a previously very Linux-friendly notebook becoming very Linux-unfriendly might be, that cause would seem to be further upstream than Ubuntu or Debian themselves.  Curious.

Hmmm .... The hardware is fine.  It all works perfectly with earlier distros and Win 7.  Curious.

---

