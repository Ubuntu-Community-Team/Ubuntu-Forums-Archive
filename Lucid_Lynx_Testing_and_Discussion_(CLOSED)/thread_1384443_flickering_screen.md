---
title: "flickering screen"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jochem on 2010-01-18
Not sure if this is the right section, but I upgraded to lucid lynx, and now my screen starts flickering as soon as GDM is loaded.
It flickers like 80% of the time. 

It occures when:
- I boot with the latest kernel (2.6.32.10), with kernel 2.6.31 everything is fine. Before the upgrade, everything was fine too.

When I open the start menu, or some other window/menu, it suddenly stops. When I use the keyboard, it almost always starts again.

I'm using an Acer Aspire 1810TZ:
- intel gs45 chipset
- intel 4500MHD graphics card

jochem@jochem-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Help appreciated :S

---

### Post by phenest on 2010-01-18
Have you checked the screen refresh rate?

---

### Post by DLGandalf on 2010-02-07
this has nothing to do with refreshrate
some parts of the screen are repainted in slomo, and artifects show until you switch to a VTTY a couple of times to remedy this,
I do wonder if this is hardware related because I've got the exact same notebook and haven't found anyone (till this thread) with the same issue.

---

### Post by phenest on 2010-02-08
I'm getting flickering with occasional graphic corruption. You're right that refresh changes nothing. It may have something to do with xorg, but I'm not certain.

---

### Post by DLGandalf on 2010-02-08
I Just put some effort into finding a solution as I found this thread. 
It appears to be the kernel probably the intel kms framework isn't working correctly in 2.6.32
switch to 2.6.33rc7 from the kernel ppa, solved my issues.

---

### Post by jochem on 2010-03-07
Hi everyone, it's been a few weeks since I replied to this topic. Thanks DLGandalf for your help and replies.

**Kernel 2.6.33 indeed fixes it** (I do get a few errors during boot, "ureadahead" and "ureadahead-other" are terminated). 

Booting the default ubuntu kernel 2.6.32 with **kernel mode settings disabled also fixes the flickering** (add boot parameters "i915.modeset=0" to grub).

I'm not sure how good kms is, and I don't know if switching to kernel 2.6.33 will cause problems in he future.

Ideal would be if kms just works with the default kernel, **is there a kernel fix available for kernel 2.6.32**?

---

### Post by jochem on 2010-03-07
So my question is, how can I use kms with the default kernel.

---

### Post by jochem on 2010-03-09
Bump

---

### Post by pressureman on 2010-03-09
Finally... someone else with this problem. I noticed it start happening after upgrading to kernel package 2.6.32-16.24. It didn't seem to be a problem on 2.6.32-15.22.

The symptoms I notice are usually a momentary block of video corruption (often greenish) in the lower half of my screen. It's so fleeting however that I can't see what it is.

My hardware is Thinkpad T500 using Intel GM45 integrated graphics.

Edit: Just upgraded to 2.6.32-16.25 and still seeing occasional glitch :(

---

### Post by angryfirelord on 2010-03-11
I've noticed a similar problem on Lucid as well. I don't get any artifacts, but there's an annoying flicker across the screen. i915.modeset=0 didn't do anything (I'm using an Intel GMA 950).

---

### Post by jochem on 2010-03-11
Since 2.6.32.16 I don't have to add i915.modeset=0 anymore, the flickering seems to be fixed. 

Now I've got a new problem. When I boot, sometimes gdm loads, and sometimes it doesn't. Switching to tty1 and back to tty7 shows gdm. It's exactly this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523027](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523027)

So I checked if kms is actually running:


```
jochem@jochem-laptop:~$ dmesg | grep drm
[   23.286764] [drm] Initialized drm 1.1.0 20060810
[   23.389012] [drm] set up 63M of stolen space
[   24.208318] fb0: inteldrmfb frame buffer device
[   24.212740] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
**[   40.308142] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id**
```

Anyone knows whats wrong?

EDIT:
After updating, it seems to be fixed :D

Good job Canonical!

---

### Post by angryfirelord on 2010-03-14
I'm wondering if the flickering has anything to do with this bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/423873]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/423873")

Try dimming the screen and see if it makes a difference.

---

### Post by pressureman on 2010-03-23
Still seeing the random flash/tear/flicker/corruption with 2.6.32-17-generic.

---

### Post by yelvington on 2010-04-08
I have an Acer 1410 and have experienced severe flickering with Lucid Lynx. After posting a bug report with Xorg, it was suggested that a client might be responsible ... and I tracked it down to gnome-settings-daemon. Killing it immediately cleans everything up. Running it immediately sends everything straight to hell, with top reporting Xorg eats ~77% of CPU (this is a dual-core Celeron).

---

