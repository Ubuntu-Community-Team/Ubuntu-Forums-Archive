---
title: "Chip Compatibility"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by spiceskull on 2008-05-14
Hi,

I have a two-year old Packard Bell machine running Win XP under normal circumstances, and in the past I have installed various Linux flavours to great disaster (boot sector damage, no dual boot, PB insist on having a "tattoo" whatever that is)

About five months ago I successfully installed Ubuntu 710 from an ISO burnt from a download. I was amazed that the install was seamless, that a dual boot existed, and that both OS's could co-exist...at last my PB machine was allowing me to do what I wanted with it.

Two days ago I downloaded the ISO image for Ubuntu 804, and am unable to install it to the machine. I originally scrubbed the machine, so that I had a fresh install of Win XP, and was hopefully going to have a fresh install of Ubuntu - my kids do all sorts of stuff on the machine, so I wanted a completely fresh system.

As the machine booted from CD I received the following error message: "This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip" I restarted, and selected the "Check CD" option, and still got the message...

This is completely alien territory to me, so is anyone able to offer advice or help?

Thanks in advance,
Adam.

---

### Post by Partyboi2 on 2008-05-14
I suspect its to do with your network card. Someone has started a bug report [[COLOR=Blue]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223187") If you have anything to add to the report it could help to hopefully sort the problem out. You could try booting with   brokenmodules=8139too as a boot option. To do this when you are at the main menu press F6 and at the end of the line add```
brokenmodules=8139too
``` then press enter to boot. This works for suse but not sure if it will work or not for ubuntu.

---

