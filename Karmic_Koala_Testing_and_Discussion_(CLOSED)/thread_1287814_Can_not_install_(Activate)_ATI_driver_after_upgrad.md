---
title: "Can not install (Activate) ATI driver after upgrading to Karmic Beta."
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-10
Hi
I upgraded to karmic beta and now I want to install the ATI driver for my graphic card.

I tried using System>Administration>Hardware Drivers and then I select the ATI/AMD proprietary FGLRX graphic driver and pressed the activate button. It asked for password and then nothing happened.

It didn't install the driver, I tried the same procedure more than once without any luck.

I download the latest driver (ati-driver-installer-9-9-x86.x86_64) from AMD website and tried to install it. the installation procedure went smoothly. I restart the computer and nothing the driver was not installed. I tried to run ATI configuration applications and the failed to start without any error.

I tried the above procedure several time, I purged the current drivers and trid again, I removed the xorg.conf file and tried.... none of them worked.

My vga cart is ATI Radeon HD 3470.

Thanks.

---

### Post by legolas_w on 2009-10-10
It looks like that there is no driver for the current kernel version.

[http://grelbar.net/archives/271](http://grelbar.net/archives/271)

The above blogger explains that we may need to wait more before we could use ATI drivers in Karmic.

Thanks.

---

### Post by emarkay on 2009-10-10
I have no probs with my HD2600XT card - Don't use the ATI driver - the Ubuntu "Restricted Driver" is ACTUALLY Cadalyst 9.10!  Just install it!  :)

---

### Post by DougieFresh4U on 2009-10-10
Using ATI Radeon HD3200 and fglrx is working fine with the .13 kernel on my 64 & 32 bit

---

