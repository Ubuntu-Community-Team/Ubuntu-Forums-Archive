---
title: "[SOLVED] Machine suddenly stopped booting after &amp;quot;checking if image is initramfs&amp;quot; mess"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Levander on 2008-03-26
I've been messing around with a Gutsy install on a box.  A few weeks ago I started having problems rebooting it.  I'd have to go into grub and erase the "quiet" and "splash" kernel options and replace them with "nosplash".  Or sometimes I'd just have to boot into recovery mode.  This worked fine until tonight.

Now when I boot, with "nosplash", the messages pause around a "boot eip processor" something message.  I can read the screen when it pauses.  A few lines above that message, there's some "no DSDT.aml file found" message.  After that pause, a bunch of messages flash by.  The last one is something like "checking if image is initramfs... it is".  Then, the computer blinks off and I'm back at the BIOS boot screen in a second.

I'm thinking my computer started getting messed up a couple of months back when I install the mythbuntu-desktop package.  When I removed that there was problems booting and there were a couple of things I had to fix manually.  One of them was something like the video driver was being loaded wrong and so loading the usplash screen would hang the box during boot.  And, I've noticed lately that for some reason when my computer boots, the mythbuntu usplash screen is back.  I have no idea why that's back.

Anyway, I remember when I had to play with usplash before that there was some reason it had to run initramfs to create some boot image or something.  

Is it possible to change the usplash on my computer from the LiveCD?  I'm thinking if I do this, initramfs will be re-run to generate whatever it is it generates and maybe my machine will boot again?

I'm really trying to avoid doing a complete reinstall.  Hardy's coming out in a little bit and I was going to waste time doing a complete reinstall when Hardy comes out.  That's the point I'm going to try to move from my current 32 bits to 64 bits.

While my computer is having trouble booting I don't have ready access to a PC.  So, I'm hoping someone can point me to some (at least rough) step by step instructions on changing usplash from the LiveCD?

Really though, any hints are appreciated.

---

### Post by Levander on 2008-03-30
Well, I found out the problem.  One of my hard drives is going bad.  It's not the one with root or boot on it.  Actually, it's from an old install of Linux on an old hard drive.  And, when I originally install LInux on the new hard drive in this machine, that old hard drive was still in here.  During the Linux install on the new hard drive, when it was installing grub it picked up on the fact that there was an install of Linux on the old hard drive, and added all the kernels installed on that old hard drive to grub/menu.lst.

I'm guessing initramfs was trying to access that old hard drive because it was included in grub/menu.lst.  And, when the hard drive went bad, it caused initramfs to crash.

I thought about entering a bug on launchpad, but I looked at the bugs there and they seem to be being reported at a fairly low level.  The guys who are reporting bugs are at a much lower level than me.  I just think there should be some kind of warning or something letting you know what the machine is doing when it boots up.  Just saying, "checking if image is initramfs" and then crashing because an auxillary hard drive went bad is pretty vague.

Anyway, unplugging the old hard drive and rebooting fixed it.

I don't know if the old hard drive would have caused the problem or not if it wasn't in grub/menu.lst.

---

