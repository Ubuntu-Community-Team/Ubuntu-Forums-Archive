---
title: "Feisty Installation Problem?"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by podister on 2007-08-08
What I'm getting is strange and I don't know if this is an install problem or something else.  I'm trying to install 7.04 64bit

I stick the CD into the drive and reboot.  Ubuntu loads just fine.  I can use everything without issues.

I install, and the install goes just fine, without issues.

Install completes, I reboot, GRUB comes up and I boot to Ubuntu.

And it then takes something to the tune of 1.5 hours to get the login screen.

After login, after 15 hours of ubuntu STILL not getting the desktop loaded, I powered down, and reinstalled ... with the same problem.

I tried installing 7.04 32bit ... same problem.

My machine is an emachines with a 64bit Athlon with 1gig of ram and an ATI graphics card with 256mb. graphics memory  The HD is 140gb and is split in half (half for windoze and half for ubuntu, and I'm just using the default ext3 format).

I've installed ubuntu probably a dozen times without a hitch on other machines.  I don't understand why the OS would run fine from the cd and choke running off of the HD.  Could this be some odd compatibility issue I've not heard of?

Any help here is appreciated.

---

### Post by dabl on 2007-08-08
Wow, that is crazy.  I recently put Kubuntu Feisty 32-bit on an emachines PC with no problem, but that one had an Intel video chip.  Which makes me wonder about that ATI chip ...

If you would reconfigure it as a VESA display, and the problem goes away, that would limit the issue down to the video display system.  To do that, boot "recovery mode", login at the text prompt, and enter ```
sudo dpkg-reconfigure xserver-xorg
```

On the first screen, choose "NO" to auto-detecting the display, and on the second screen choose "VESA" as the display type.  Then go through the rest of the script accepting defaults, until you get to the "screen" part of it.  Pick a single resolution that you can tolerate for awhile, like 1024 x 768, and then pick suitable refresh rates for your LCD or CRT.  When the script completes, it will dump you back to the CLI, aka text prompt.  At this point you can do ```
startx
```and you should get a reasonable GUI, and no more 15 hour boot cycles.

But of course, you won't be taking advantage of whatever accelerated/3D graphics that ATI chip is capable of.  You'll have to chase an ATI driver solution to do that.

HTH!  :)

---

