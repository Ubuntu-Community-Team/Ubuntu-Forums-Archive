---
title: "How best to transfer Ubuntu installation to new computer"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by nirkolous on 2010-10-25
I was running Ubuntu fine on an old box of mine for about a year. The box was running two old processors and a very generic video card embedded in the motherboard.

I have a new computer I built not too long ago that I was using to run Windows 7, running an AMD X3 processor and a Radeon HD5670 graphics card.

I would like to use this computer to run my Ubuntu operating system from my hard disk from the old computer. I was hoping to just plug in the hard drive and have Ubuntu recognize the new hardware.

However, when I boot from the hard disk the initial Ubuntu boot screen shows up, and then the screen goes blank. The screen turns off after a few seconds for lack of signal. 

I believe this is an incompatibility with my video card, because if type in my password a few seconds after the screen goes blank, I can hear my hard drive whirl away loading.

Is there any way to "safe boot" Ubuntu so I can configure the hardware, or another means to correct the hardware issues? (Please don't ask me to stick it back in my old computer and configure from there -- the parts have already been salvaged.)

---

### Post by nirkolous on 2010-10-25
Hold left shift. They don't teach you that in grade school.

---

### Post by oldfred on 2010-10-26
Shift (hold not tap) gets you to the grub menu, but then you need to add a parameter. Mine was nomodeset, yours may vary.

On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

Not sure with Radeon you have a driver or just permanently add a parameter to grub.

---

