---
title: "Blank screen after May 30 xorg update"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by hreichgott on 2011-06-01
Hi,

Solved this one myself, but thought I would post in case anyone else had the same problem. I notice there are a lot of "blank screen" issues lately esp. with Radeon cards.

I have an Acer Aspire 5253 with an ATI Radeon 6310 graphics card and HD 1366x768 resolution. I originally installed Ubuntu 10.10 on it (most recent version at the time). The default driver (opensource radeon) couldn't handle 1366x768 resolution so I tried installing the ATI proprietary Catalyst (fglrx) driver through the "Additional Drivers" menu. That resulted in correct resolution, but an annoying "unsupported hardware" watermark on the bottom corner of the screen. Then I went to ATI's website and downloaded their Catalyst driver and ran it directly. Problem solved.

Upon upgrade to 11.04, the screen was blank upon boot. I rebooted into low graphics mode, found that the Catalyst driver had been uninstalled, went to ATI's website again, downloaded and reinstalled the Catalyst driver. All was well.

On May 30 xorg was updated. Upon the first reboot after the update, I had a blank screen. I tried going to ATI's website and reinstalling the Catalyst driver, but it did not solve the problem. I uninstalled the driver completely, reverted to the opensource radeon driver, and had working 2D graphics--but no 3D/OpenGL support, so some programs wouldn't run. I then tried installing Catalyst from the "Additional Drivers" menu (I'm using Ubuntu Classic instead of Unity). That solved the problem. No annoying watermark any longer, for some reason.

So if anyone else is having the same problem, do try installing the Catalyst driver from the "Additional Drivers" menu. I do not have enough understanding to know what's different when it's installed this way vs. through the download from the ATI website, or apt-get install fglrx, for that matter. But it does appear to be different.

---

