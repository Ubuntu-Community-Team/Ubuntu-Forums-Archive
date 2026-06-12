---
title: "ubuntu software center progress indicator strange vivid vervet"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2015-07-13
Since upgrading to 15.04 Vivid Vervet I have observed strange behavior by the installation progress indicator in Ubuntu Software Center.  Instead of an expanding orange bar that gradually fills up the gray rectangle instead there is only a tiny white vertical dash that moves along the top of the rectangle.  Everything works but obviously there has been some change in the implementation of the GUI support for this kind of progress indicator.  It may be only cosmetic but I doubt this was the intention of the developers.

---

### Post by v3.xx on 2015-07-14
I do not know much about the software center, [never use it.]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9")

But my first guess would be to try a reinstall of the software center.

---

### Post by Vladlenin5000 on 2015-07-14
Upgraded a few and never noticed such behaviour.
Could it be you had a proprietary graphics driver before and wasn't reinstalled for the new kernel?

---

### Post by 7-webmaster on 2015-07-15
> **Vladlenin5000 said:**
> Upgraded a few and never noticed such behaviour.
Could it be you had a proprietary graphics driver before and wasn't reinstalled for the new kernel?

Good thought.  I have been using the recommended X.org driver for the AMD/ATI graphics on my laptop for several releases now because it worked better for most purposes than the closed fglrx driver.  Prior to 15.05 neither driver would reliably resume from suspend on my hardware, a rather important issue on a laptop, but there has been a lot of work put into AMD support and I was just mentioning this little peculiarity.

---

