---
title: "If I upgrade from Ubuntu 12.10 to 13.04 will my drivers be effected"
date: 2013-05-26
forum: Installation &amp; Upgrades
---

### Post by patagriff on 2013-05-26
I want to upgrade from 12.10 to 13.04. However, I'm worried that something in the upgrade process will make it necessary to reinstall the proprietary driver for my Broadcom wireless adapter. I only have access to the internet through wifi. I have no ethernet connection at my immediate disposal, therefore would be dead in the water if the upgrade process made it necessary to reinstall this driver.

Does an Ubuntu upgrade effect proprietary drivers that are currently installed?

Will this upgrade make it necessary to reinstall VLC media player, Google Chrome and other third party software I have currently installed?

---

### Post by DJWYMAN on 2013-05-26
it should not get rid of any of that stuff.  how ever I would make a back up just in case.  also if you have your install cd you made to install ubuntu the broadcom drivers should have been on there or they used to be anyway.

---

### Post by fantab on 2013-05-27
If you are looking to upgrade from 'update-manager' then it is recommended that you disable any external ppa that you have, like google chrome for instance. You can do this from 'Software Center' -> Edit -> 'software sources'. Later, when the Upgrade is successful you can re-enable them. Then you have to edit /etc/apt/sources.list to change the distribution from 'quantal' to 'raring'. 

And Yes you may probably need to re-install those prorietory drivers.

---

### Post by patagriff on 2013-05-28
Thanks folks. That's one yes and one no. I'll wait. There's no hurry to upgrade so why take the chance.

---

### Post by Mark Phelps on 2013-05-28
I've been updating Ubuntu versions for seven years -- and every update brought with it one problem or another.

So, I learned early on to make an image backup of my most current setup using Clonezilla.  That way, if the update goes badly (and they sometimes do), restoring a working system only takes a few minutes.

---

### Post by Cheesehead on 2013-05-28
> **patagriff said:**
> Does an Ubuntu upgrade effect proprietary drivers that are currently installed?

Yes.
A 'driver' is a kernel module. Kernel modules must be replaced (or recompiled) every time the kernel is changed. Upgrades change the kernel.



> **patagriff said:**
> Will this upgrade make it necessary to reinstall VLC media player, Google Chrome and other third party software I have currently installed?

Depends on how they were installed.

Some applications are compatible with multiple versions of Ubuntu. Some are not.
If the application If you installed an application from the Ubuntu Software Center (including partners), then it should upgrade automatically with the rest of the system, and without trouble.
However, if you installed it using some PPA or web page voodoo or third-party repository or mysterious-origin .deb file or tarball, then it's chancy. Generally, it's safer to uninstall unknown-origin applications before updating, then reinstall them after the update.

---

### Post by patagriff on 2013-07-03
Solved: Went ahead with the upgrade. VLC media player stayed put. It was not necessary to re-install my proprietary Broadcom wireless adapter driver. 

The upgrade went of with only one hitch. It was necessary to download Google Chrome 64 bit for Ubuntu from the Chrome website because it was unavailable from the Software Center. Minor. All in all, it worked magnificently.

I have noticed only a couple of insignificant cosmetic differences between 12.10 and 13.04.

---

### Post by Bucky Ball on 2013-07-03
Two things: 

I strongly discourage upgrading via a wifi connection.
Upgrades can be problemmatic and a clean install is just that, cleaner. Better option.

---

### Post by hans12345 on 2013-07-15
> **Bucky Ball said:**
> Two things: 

I strongly discourage upgrading via a wifi connection.
Upgrades can be problemmatic and a clean install is just that, cleaner. Better option.

If you have AMD ATI graphics, avoid ALL updates.

12.04 was lovely

 I upgraded from Ubuntu 12.04 to 12.10, with a wifi update, lots of pain from ATI graphics.

 I upgraded from Ubuntu 12.10 to 13.04 with a wifi update since I wanted to keep my working drivers, with an idea to avoid the pain, but I have even more this time.

Next time I get to a LTS version, I'll stay with it and not upgrade until I have to.

---

### Post by hans12345 on 2013-08-04
Maybe a little harsh. My problem was due to AMD declaring my Radeon 4200 as 'legacy' and thus unsupported.

In the end I had to do a clean install of 13.04.

---

