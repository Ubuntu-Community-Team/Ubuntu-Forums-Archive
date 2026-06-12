---
title: "Breezy-to-Dapper fglrx problem"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2006-11-22
I did an upgrade from Breezy to Dapper using the "one-click" method.  I am now having severe problems with freezes and crashes.  They seem to be closely associated with the video system.  For example, starting glxgears from a terminal freezes at once.  Even starting glxinfo freezes.  Many applications that seem to be working suddenly freeze or crash (black screen) when they try to make some new screen display.

fglrxinfo shows (correct, so far as I can glean):

display:  :0.0   screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version: 2.0.5814 (8.25.18)

My "card" is an on-board X200.  I had installed the fglrx driver, v. 8.25.18, and it worked fine under Breezy, with acceleration--glxgears churned fast and smooth.  The xorg.conf file was *not* changed in the upgrade.

I can avoid the problems by booting into the previous kernel, but then some other things (such as sound) don't work, and in any event that defeats the purpose of upgrading.

I have seen numerous threads about lockups with the fglrx driver, but what I don't get is why, since it worked perfectly under Breezy, the upgrade to Dapper has caused all this, with no xorg.xonf file changes.  (I have Attached a copy of that file.)

I am not well conversant with Linux in general or Ubuntu in particular, so any suggestions need to be put in basic and exact terms.

I thank all who read this.

-----------------------------------
Later-added info:

I did some poking about and discover that there are apparently kernel-specific versions of fglrx, in the folders:

/lib/linux-restricted-modules/2.6.12-10-686/fglrx

  and

/lib/linux-restricted-modules/2.6.15-27-686/fglrx

The older set has several files not in the newer set, and has a lib file of some sort--

  libfglrx_ip.a.GCC3

that is GCC4 in the newer set.

I suppose the problems reside here somehow, but what do I do to get back proper functionality?

Thanks again.

---

