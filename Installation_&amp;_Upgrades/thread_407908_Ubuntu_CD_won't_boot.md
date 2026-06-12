---
title: "Ubuntu CD won't boot"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by Luffer on 2007-04-12
I have created a CD with the Ubuntu 6.10 distribution on it. I've tried running it on my PC and after selecting:

- Start or install Ubuntu

I see the logo and a progress bar, after a minute or so the screen goes blank and there is a flashing cursor in the top left of the screen. Nothing happens and I have to reset to get back to the boot menu. I've tried this a few times and get the same result every time, I've also tried the "safe graphics mode" option, but it makes no difference.

I'm not new to PCs or the technical aspects of them, but I'm a complete Linux novice. I've used Unix terminals in the past so I figured I'd give it a shot. But I can't even get to a position where I can install the OS.

I've had the disc running fine in another machine and it gets to the Linux desktop with no trouble. My PCs specs are as follows:

AMD Athlon 2600+
1Gb RAM
160Gb HDD
ATI Radeon 9800 Pro
Realtek AC'97 Onboard Sound

It currently has WinXP on the HDD but there is plenty of free space and I want the Ubuntu installation to use the whole disk when it installs. I no longer need that PC and I'm just going to use it to experiment with Linux.

Can anyone help? If I can't get past the boot menu, I have no hope!

Regards,
James

---

### Post by taurus on 2007-04-12
Sounds like the desktop CD/LiveCD is having a little technical difficulties with your graphic card.  And since you want to install Edgy on that machine, you should use the alternate CD instead.  It allows you to install from the CD directly without booting into Gnome first.  Also, it uses text base installer but real easy to follow.

Don't forget to burn it at a slow speed like 4x.

---

### Post by Luffer on 2007-04-12
Hmm, more questions:

Is there nothing I can go to get this CD to boot to the desktop? I know the CD is fine because it boots on another machine, and it reports no problems when I "Check CD for defects".

Where do I find the alternate CD to download? I got the desktop edition from the Ubuntu website, but can't see that option listed.

If it's having technical difficulties with my graphic card, how will it be any different with this other version? Surly it will still encounter the same problem of booting to the desktop at some point and fall over there instead?

Perhaps a slightly naive question this, but I thought Ubuntu was supposed to be a user friendly Linux distro. That's certainly what I've been reading, if that's the case, how can it have problems with a mainstream gfx card like the Radeon?

Finally, what's Edgy? I've seen it mentioned a few times but I can't figure it out.

Regards,
James Luff

---

### Post by taurus on 2007-04-12
[http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/edgy/)

---

### Post by Luffer on 2007-04-13
Thanks, that points me in the right direction for the distribution. Can anyone else help with some of my other questions?

Regards,
James

---

### Post by epiphiny on 2007-04-13
I had the exact same problem with my ati radeon 9200 pro.  This was casued (I think) by having a very similar chip on my motherboards onboard graphics chip; try removing your PCI graphics card, plugging your monitor into the motherboard and booting.  This should allow you to boot.

If it works, then install as normal and use the vesa drivers (they are pretty much foolproof).  Then reinsert the card, and plug your monitor into it.  Your system will probalby crash at boot, but you will get a nice juicy xorg log.  Read through it, and look for the pci address of your 'real' card.  For example, I got something along the lines of;
ATI radeon (9200 Professional Pro) blah
PCI: 4:6:1

Find there it says that, and plug those numbers after the pci into your xorg.conf file.  You should be able to do this from the shell you get after xserver cant load.  If not, try rebooting to the failsafe terminal offered at grub.

Hope this is vaguely useful/coherrent, it seems that the installer really doesn't play well with cheaper, older ati cards.

---

### Post by Luffer on 2007-04-13
The motherboard doesn't have an on-board gfx chip, so I can't remove my AGP card; I won't see anything!

I wouldn't call the 9800 Pro particularly old or cheap, it was a pretty good offering 2 - 2 and a half years ago. Unless that **is** considered to be old?

Any other suggestions or solutions?

Regards,
James

---

### Post by epiphiny on 2007-04-13
You'd have thought so, but there is little support for the 9xxx cards.

Anyway, if you don't have onboard graphics, your only option is a text-only install via the alternative cd.

Don't worry, once its installed its exactly the same as an install from the live cd.

If you can't get x to load at boot, try setting your driver in xorg.conf to use vesa - its saved me countless times!

---

### Post by Luffer on 2007-04-13
I guess that's what I'll have to try then, but I wanted to see it working before I installed it.

As I have been advised that ATI cards seem to be poorly supported, I remembered I have an old NVidia GeForce Ti200 gfx card. Thought I'd bung that in the machine to get it to boot.

First attempt I got exactly the same result so I rebooted again. The second time I got to a brown desktop and a mouse pointer (which I could move) but nothing else appeared. Just a solitary mouse pointer on a brown screen.

This reminded me of the very first time I tried to boot the CD on the computer with the ATI card.  I actually saw a round mouse pointer which had a sort of dial going round it, but that was against a black screen and nothing else happened.

Does this mean anything to anyone? What the hells going on here?

Regards,
James

---

