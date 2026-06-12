---
title: "Black Screen and Logon Hang"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by squidie on 2011-08-02
**  **

Hi,
  

I’m packing an Intel Core2Duo 2.00GHz, with an onboard GeForce 8200M G, with 3GB of DDR2 833mhz RAM.
  

I’ve installed “successfully” 11.04, now I’m having the common issue where I’m having to use the nomodeset selection on install and remove the quite –splash and install. It always installs fine this way... Until I go to boot. Sometimes I’ll get the ubuntu sound along with the loading screen or the ubuntu sound along with a black screen.
  

I’ve been looking around for a while at the possibilities and I’m pretty sure it’s because of the on-board nvidia processor, though most options I’ve seen haven’t worked for me.
  

What do you guys reckon?
  

Thanks

---

### Post by MAFoElffen on 2011-08-02
> **squidie said:**
> 

Hi,
  

I’m packing an Intel Core2Duo 2.00GHz, with an onboard GeForce 8200M G, with 3GB of DDR2 833mhz RAM.
  

I’ve installed “successfully” 11.04, now I’m having the common issue where I’m having to use the nomodeset selection on install and remove the quite –splash and install. It always installs fine this way... Until I go to boot. Sometimes I’ll get the ubuntu sound along with the loading screen or the ubuntu sound along with a black screen.
  

I’ve been looking around for a while at the possibilities and I’m pretty sure it’s because of the on-board nvidia processor, though most options I’ve seen haven’t worked for me.
  

What do you guys reckon?
  

ThanksUse the nomodeset boot optiion again on reboot after the install (initially)... refer to the first 3 posts of this stcky:
[COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank ]("http://ubuntuforums.org/showthread.php?t=1743535")

just long enough to get booted... Then install the nvidia drivers via the Additional Drivers applet under System >Administration... or in post #280 of that sticky.

---

### Post by squidie on 2011-08-02
Thanks, using this I&#8217;ve been able to boot in low graphics mode and it&#8217;s already told me I&#8217;m not up to spec with that. I&#8217;m going to install the recommended drivers then reboot and see if it works

Seems to be working now guys, step one and two helped me fix this

Thanks again

---

