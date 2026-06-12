---
title: "Lucid beta-1 with nvidia MX440 - anyone able to boot from liveCD without 'nomodeset'"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CryptoPaul on 2010-03-30
I've a rather elderly PC with a nvidia MX440 video card.

This hangs after the splash screen when booting from the lucid beta-1 desktop i386 liveCD, (funky horizontal lines on the monitor and a dead keyboard,) unless I use 'nomodeset'.

I'm limited to running from the liveCD on this PC at the moment, not yet wanting to install lucid.

Anyone else with an MX440 card having the same problem, as I'm trying to establish if this is common to the MX440, or unique to my setup. I have a couple of other PCs with GeForce 8600 GTS cards which boot ok from the same liveCD.


Paul.

---

### Post by a.walker on 2010-03-30
> **CryptoPaul said:**
> I've a rather elderly PC with a nvidia MX440 video card.

This hangs after the splash screen when booting from the lucid beta-1 desktop i386 liveCD, (funky horizontal lines on the monitor and a dead keyboard,) unless I use 'nomodeset'.

I'm limited to running from the liveCD on this PC at the moment, not yet wanting to install lucid.

Anyone else with an MX440 card having the same problem, as I'm trying to establish if this is common to the MX440, or unique to my setup. I have a couple of other PCs with GeForce 8600 GTS cards which boot ok from the same liveCD.


Paul.

I also have an elderly computer, but it has an nvidia geForce 5200 in it (I use the 173 driver). The liveCD would boot only with 'nomodeset'. Once I installed on my HD and updated I was able to boot normally and install the proprietary drivers. The boot problems were fixed after updating.

---

### Post by tuxar on 2010-04-01
> **CryptoPaul said:**
> I've a rather elderly PC with a nvidia MX440 video card.

This hangs after the splash screen when booting from the lucid beta-1 desktop i386 liveCD, (funky horizontal lines on the monitor and a dead keyboard,) unless I use 'nomodeset'.

I'm limited to running from the liveCD on this PC at the moment, not yet wanting to install lucid.

Anyone else with an MX440 card having the same problem, as I'm trying to establish if this is common to the MX440, or unique to my setup. I have a couple of other PCs with GeForce 8600 GTS cards which boot ok from the same liveCD.


Paul.

I have same issue, please try the next:

1.Boot the LiveCd
2.Choose English
3. Press F6 without check anything and escape.
This step must show the booting command line.
4. Cut[COLOR=Lime] **quite splash --**[/COLOR] from the line.

This work for me with lucid-desktop-i386.iso (20100324).

---

### Post by CryptoPaul on 2010-04-01
> **tuxar said:**
> I have same issue, please try the next:

With an MX440 video card?

> 
1.Boot the LiveCd
2.Choose English
3. Press F6 without check anything and escape.
This step must show the booting command line.
4. Cut[COLOR=Lime] **quite splash --**[/COLOR] from the line.

This work for me with lucid-desktop-i386.iso (20100324).

Still hangs with the funky coloured screen and a locked keyboard - just don't get the hi-res splash screen ;)

I've seen in[ this post ]("http://ubuntuforums.org/showthread.php?t=1436466")reports of problems with the proprietary (Nvidia 96) driver that I would use with this PC after I've installed lucid, so for the moment, I'll wait for the final release and see what that brings forth.

Thanks - Paul

---

### Post by camiladrian on 2010-04-12
> 1.Boot the LiveCd
2.Choose English
3. Press F6 without check anything and escape.
This step must show the booting command line.
4. Cut[COLOR=Lime] **quite splash --**[/COLOR] from the line.

This work for me with lucid-desktop-i386.iso (20100324).                      that work for me
also work the nomodeset
without any of this 2 workarounds im stuck with the logo screen seen while booting
beta2 in geforce 7000m

pd never had problem with livecds before, aside of screen resolution and wifi, but both were fine in 9.1

---

### Post by dino99 on 2010-04-12
nomodeset is outdated now, instead use yourchipsetname.modeset=0 format.

yourchipsetname is i915 or radeon or else, you have to identified it.

---

