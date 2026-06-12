---
title: "Last intel driver update kills compiz"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2010-04-13
With last intel driver update compiz does not work anymore.
The error is:
```
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```
Found in .xsession-errors

There is a launchpad entry for this issue [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/542442) (but I think was solved in the past update...)

Intel driver is:
```
xserver-xorg-video-intel:
  Installed: 2:2.9.1-3ubuntu3
  Candidate: 2:2.9.1-3ubuntu3
  Version table:
 *** 2:2.9.1-3ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status

```

My card:
```
VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Anyone has the same issue?

---

### Post by Linux000 on 2010-04-13
Same here, I have an intel gm965, and trying ```
SKIP_CHECKS=yes compix
``` doesn't work anymore.

---

### Post by humble_coffee on 2010-04-14
Yup, exactly the same problem.

---

### Post by coffeecat on 2010-04-14
> **humble_coffee said:**
> Yup, exactly the same problem.

With which Intel gfx chipset?

Compiz is still working fine here with the 2:2.9.1-3ubuntu3 version of xserver-xorg-video-intel. My intel gfx from lspci:

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)Looks as though this could be a problem with older Intel graphics.

---

### Post by timosha on 2010-04-14
Same here:

I removed xserver-xorg-video-intel 2:2.9.1-3Ubuntu3 and reinstalled  xserver-xorg-video-intel 2:2.9.1-3Ubuntu1 out of cache, together with xserver-xorg-video-all. Everything is working fine again.

---

### Post by zneastman on 2010-04-14
Same here, running a Thinkpad x40 with an Intel 855GME.  Downgrading to xserver-xorg-video-intel 2:2.9.1-3Ubuntu1 allows compiz to run again.

---

### Post by timosha on 2010-04-14
I opened a bug :  [https://bugs.launchpad.net/bugs/563020](https://bugs.launchpad.net/bugs/563020)

Please click on "this affects me too" otherwise they won't do anything about it.

---

### Post by glasen on 2010-04-14
Please just read the changelog of the driver, instead of opening a new bug report :

>   [Christopher James Halse Rogers]
  * debian/patches/107_disable_dri_on_845_855.patch:
    + Disable DRI on i845 and i855 chips.  Works around the stability problems
      these chips have in Lucid (LP: #541492, LP: #541511).


This means, no compiz and no 3D-accel at all for this types of chipsets.

PS :

If you want a stable version of the intel driver (version 2.11git, updated regularly) which works nearly perfectly with KMS(*), you can try the following PPA :

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

(*) On my Notebook (Dell Latitude D505, Intel 855GM-chipset), the system crashes when i'm closing the lid. Going into suspend mode by using the logout menu and than closing the lid works perfectly.

---

### Post by timosha on 2010-04-14
> **glasen said:**
> Please just read the changelog of the driver, instead of opening a new bug report :



This means, no compiz and no 3D-accel at all for this types of chipsets.



When this so called "workaround" causes a garbled screen after resume from suspend/hibernate then it is a bug ! It is not the chipset which is unstable, these chipsets are stable since the day they were designed. It is Lucid which is unstable.

Apart from that, version 2:2.9.1-3Ubuntu1 works just excellent.

---

### Post by humble_coffee on 2010-04-14
> **coffeecat said:**
> With which Intel gfx chipset?


Pretty sure it was exactly the same as dentaku65. I'm now away from the computer so can't check. Definitely a fairly old model anyway.

---

### Post by dentaku65 on 2010-04-14
> **glasen said:**
> Please just read the changelog of the driver, instead of opening a new bug report :



This means, no compiz and no 3D-accel at all for this types of chipsets.

PS :

If you want a stable version of the intel driver (version 2.11git, updated regularly) which works nearly perfectly with KMS(*), you can try the following PPA :

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

(*) On my Notebook (Dell Latitude D505, Intel 855GM-chipset), the system crashes when i'm closing the lid. Going into suspend mode by using the logout menu and than closing the lid works perfectly.

Works pretty good with my card your driver... I'm just a little be scared if, for some reason, I need to revert the driver with the official one; with my card until beta 2 I was not able to do nothing after grub, even in recovery mode... but I will keep your version because without compiz my box is too slow (metacity is really slow here),

thx

---

### Post by davidmohammed on 2010-04-14
This driver update is the worst I've seen since the mess of intel drivers during Jaunty.  Youtube and other videos can no longer be viewed in fullscreen.

Dreadful decision.  This one decision makes me want to revert back to Karmic!

It needs to be reverted immediately.

---

### Post by timosha on 2010-04-14
Apparently this "update" is a workaround to cure other problems. This raises the question: what is worse? The medicine or the disease?

---

### Post by davidmohammed on 2010-04-14
Given the limited number of reports from intel users I strongly suspect the silent majority are having no issues... until now.  Canonical are going to get hammered by bad press again by effectively reverting back to the intel-jaunty fiasco.

---

### Post by timosha on 2010-04-14
> **dentaku65 said:**
> Works pretty good with my card your driver... I'm just a little be scared if, for some reason, I need to revert the driver with the official one; with my card until beta 2 I was not able to do nothing after grub, even in recovery mode... but I will keep your version because without compiz my box is too slow (metacity is really slow here),

thx

I installed this driver on a second test system which was also infected by the "update". Works perfectly including resume from suspend when closing/opening the lid.

Thanks a lot :popcorn:

---

### Post by dentaku65 on 2010-04-14
> **timosha said:**
> Apparently this "update" is a workaround to cure other problems. This raises the question: what is worse? The medicine or the disease?

Timosha, do you think that is the final one? I really hope not :-)
...even if the release date is so close.

---

### Post by Dauthi4 on 2010-04-15
> **glasen said:**
> Please just read the changelog of the driver, instead of opening a new bug report :



This means, no compiz and no 3D-accel at all for this types of chipsets.

PS :

If you want a stable version of the intel driver (version 2.11git, updated regularly) which works nearly perfectly with KMS(*), you can try the following PPA :

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

(*) On my Notebook (Dell Latitude D505, Intel 855GM-chipset), the system crashes when i'm closing the lid. Going into suspend mode by using the logout menu and than closing the lid works perfectly.

Thank you for your ppa.

The problem is when I update using this ppa and reboot, it works until the boot is complete.
Then, just before displaying the desktop, it starts to flicker between a terminal and Plymouth.

I tried with kernel 2.6.32 and 2.6.34 with no luck at all.

Any ideas ?

---

### Post by humble_coffee on 2010-04-26
Well luckily they realised that disabling this was a bad move and have reverted the change.

[https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.9.1-3ubuntu5/+changelog](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.9.1-3ubuntu5/+changelog)

Compiz is now working fine for me.

---

### Post by reidi on 2010-04-27
> **glasen said:**
> 

PS :

If you want a stable version of the intel driver (version 2.11git, updated regularly) which works nearly perfectly with KMS(*), you can try the following PPA :

[https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

(*) On my Notebook (Dell Latitude D505, Intel 855GM-chipset), the system crashes when i'm closing the lid. Going into suspend mode by using the logout menu and than closing the lid works perfectly.

Hooray!  The driver and library available on the above site worked for me.  I was unable to boot into the latest kernel 2.6.32-21-generic #32 without manually configuring an xorg.conf and forcing the vesa driver.  With this fix I can use the latest kernel without any fussing with kernel mode settings or dumbed-down drivers, AND I can use compiz.

Why isn't Ubuntu using this Intel driver?

Highly recommended!

Fujitsu Lifebook S series
Intel 82852/855GM Integrated Graphics Device (rev 02)

---

