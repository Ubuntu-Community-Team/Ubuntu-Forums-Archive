---
title: "Nvidia driver install for old GPU"
date: 2021-01-24
forum: Installation &amp; Upgrades
---

### Post by kjmarti2 on 2021-01-24
Hello,

I've recently brought an old laptop back to life with Lubuntu 20.04 and am trying to install the proprietary Nvidia driver for my GPU (an Nvidia Geforce Go 7950 GTX). I tried to use ubuntu-drivers autoinstall but no drivers were found. After a bit of digging, it seems the driver I need is version 304.137 which apparently is no longer supported.

I've read of people successfully patching driver 304 to work with newer kernels, but the newest ubuntu version that I found a reference to was 18.04. Is patching this driver possible in 20.04 or do I just need to give this up? Any info/advice is appreciated.

---

### Post by simon-webb on 2021-01-24
Hi there. If it were only the kernel it would be possible, either by patching the driver to build or simply by downgrading the kernel (which would be very unwise, but still possible) as you can run an old kernel on a new distro...however...in this case I think there's other crucial software (like Xorg) that has stopped working with the legacy drivers too...so it's probably not worth the hassle of trying to use that ancient driver on a modern OS. Is your laptop not working well with the nouveau driver? An "old laptop" doesn't sound like a gaming machine, and if you're not needing every bit of performance from your graphics card, the kernel's built-in nouveau driver is fine...better that the Nvidia driver, in fact, in some ways (you tend to get a nicer-looking startup with kernel mode-setting, and on many cards it's less buggy too): I have Nvidia cards on most of my computers, and could choose to install the proprietary drivers, but usually prefer nouveau. In fact, from a glance at the nouveau features matrix, it looks like your card even has vdpau acceleration in nouveau...so you'll get decent accelerated video playback too (which is more than I get on my more modern cards!).

---

### Post by CelticWarrior on 2021-01-24
> [COLOR=#000000]it's probably not worth the hassle of trying to use that ancient driver on a modern OS[/COLOR]
This^^^ exactly.
The same for any modern Windows, the versions with current support, the only drivers that work are some Windows generic ones.

---

### Post by kjmarti2 on 2021-01-24
You're probably right. The nouveau driver works well for basic use, I was just wanting to use this old laptop as a testbed for overclocking a gpu since I've never done it before and that requires the nvidia driver from what I've read. Thanks for the input, sounds like it's not worth any more of my time to research.

---

### Post by deadflowr on 2021-01-24
If you wanted to just test some things out about overclocking then install Ubuntu 16.04.
The 304 drivers still work on that system.
But you need to install the 16.04.1 ISO and nothing later like the current 16.04.6( or 7 now???)
The 16.04.1 ISO uses the 4.4 kernel series, while later versions like 16.04.6 use the [Hardware Enablement ]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")kernel series 4.15 which doe not work out of the box with the 304 driver.

The 16.04.1 ISo can be found here: [http://old-releases.ubuntu.com/releases/xenial/]("http://old-releases.ubuntu.com/releases/xenial/")
Ubuntu 16.04 is still supported for the next few months, as it reaches end of life sometime after April.

---

### Post by kjmarti2 on 2021-01-24
> **deadflowr said:**
> If you wanted to just test some things out about overclocking then install Ubuntu 16.04.
The 304 drivers still work on that system.
But you need to install the 16.04.1 ISO and nothing later like the current 16.04.6( or 7 now???)
The 16.04.1 ISO uses the 4.4 kernel series, while later versions like 16.04.6 use the [Hardware Enablement ]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")kernel series 4.15 which doe not work out of the box with the 304 driver.

The 16.04.1 ISo can be found here: [http://old-releases.ubuntu.com/releases/xenial/](http://old-releases.ubuntu.com/releases/xenial/)
Ubuntu 16.04 is still supported for the next few months, as it reaches end of life sometime after April.

Awesome, thanks for the info. I think I'll break out one of my old hard drives to install 16.04 on and play around with the gpu overclocking there.

---

### Post by O)9(yo&amp;# on 2021-01-25
I have a similar problem. My video card died, along with my power supply, putting me back on original PS and on-board graphics (Nvidia 6150se). open-source drivers don't work well with this setup, except for bodhi 5, the only system later than Ubuntu 18 that I have been able to install and use (after disabling acceleration in my browser). So I have bodhi on one SSD. I also have Ubuntu 16.04 on another SSD. that is using the Nvidia 304 driver. It's the Ubuntu 16 that uses kernel 4.4 and keeps it on that kernel. Nvidia stopped supporting that driver beyond 4.4. 

I can report that both these systems work well on my old Gateway desktop. I plan on signing up for ESM for UB. 16 in April, when it reaches EOL. I had ESM on Ub. 14 previously, but when I found I could still use the 304 driver with Ub. 16 I went with that. Eventually this old rig will die, which is why I haven't replaced the PS or video card. As long as still works on a supported Linux system, no reason to.

---

### Post by mastablasta on 2021-01-27
> **michael_diemer said:**
> 
I can report that both these systems work well on my old Gateway desktop. I plan on signing up for ESM for UB. 16 in April, when it reaches EOL..

how much does ESM cost nowadays?

> **kjmarti2 said:**
> Awesome, thanks for the info. I think I'll break out one of my old hard drives to install 16.04 on and play around with the gpu overclocking there.

i think you can overclock with nouveau as well, but as i read it it has to be incrementally increased. and it is in CLI.

---

### Post by TheFu on 2021-01-27
I think ESM on 3 systems is free. [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)
> Free for personal use

Canonical provides Ubuntu Advantage Essential subscriptions, which include ESM, free of charge for individuals on **up to 3 machines**. For our community of Ubuntu members we will gladly increase that to 50 machines. Your personal subscription will also cover Livepatch, FIPS and CIS hardening tools.

Of course, there is a privacy trade off in signing up for ESM which could be important to some people. I'm fairly certain this is 100x less than the mandated privacy sucking aspects other OSes include in their EULA.

---

