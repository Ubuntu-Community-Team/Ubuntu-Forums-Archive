---
title: "Delayed black screen when booting 64-bit Pangolin from USB. Why the delay?"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by spaceshipguy on 2012-09-01
I'm trying to install Pangolin 64 bit on my HP laptop with ATI Mobility Radeon Premium Graphics, by AMD. 

It's quite odd. I insert USB stick, switch on, press esc to boot from USB, Ubuntu boots up slowly, very slowly.

Eventually an empty desktop appears. If I move the mouse a window appears giving me the option of installing or trying Ubuntu.

I click try and the machine goes very slowly to a black screen, the fan and temperature climbing all the time, and then I switch it off in a panic because I don't want to melt my laptop.

Shouldn't the black screen of death appear straight away? Why does it wait for me to click try?

Has anyone else had this problem?
I'd love to go from Natty 32-bit to Pangolin 64-bit :-)

---

### Post by 2F4U on 2012-09-01
Try the nomodset boot option. When booting off the livecd press the space bar when you see the tiny 'human' logo down the bottom. When you get the alternate menu select boot options (F6) and select nomodeset. Continue with the LiveCD boot.

---

### Post by spaceshipguy on 2012-09-02
> **2F4U said:**
> Try the nomodset boot option.

Worked a charm, thanks, and Jupiter solved my heat issues!! :-)

---

