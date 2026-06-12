---
title: "Intrepid Ibex &amp;&amp; live cd + Broadcom drivers"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ww711 on 2008-10-08
When the Intrepid Ibex Live CD is released and used alongside a machine that contains a broadcom wirelss chipset.

How good an indication is it that, if you can load a live cd and it can automatically detect the wireless chipset and pick a wireless access point, that it will potentially work for an upgrade/fresh install. Using the live CD as a test to determine if the wireless hardware works.

---

### Post by Ayuthia on 2008-10-08
> **ww711 said:**
> When the Intrepid Ibex Live CD is released and used alongside a machine that contains a broadcom wirelss chipset.

How good an indication is it that, if you can load a live cd and it can automatically detect the wireless chipset and pick a wireless access point, that it will potentially work for an upgrade/fresh install. Using the live CD as a test to determine if the wireless hardware works.

If you do a fresh install, the wireless should work once you activate it through Hardware Drivers.  The driver that is being used is the wl driver instead of the b43 driver.

However, if you are doing an upgrade, the wireless should still work depending on what you are using (ndiswrapper, wl, b43, or bcm43xx).  The thing that I am not sure about is the upgrade of firmware for the b43 (the firmware was changed in 2.6.25).  It has been a while since I tested it out on Intrepid.  The firmware that was used in Hardy will still work in Intrepid, but you will get a message that will say that your firmware is out of date and you need to upgrade.  What this also means is that if you upgrade the firmware and upgrade to Intrepid, you will not get the wireless to work in any 2.6.24 kernel because the firmware is too new.

Hope that helps.

---

