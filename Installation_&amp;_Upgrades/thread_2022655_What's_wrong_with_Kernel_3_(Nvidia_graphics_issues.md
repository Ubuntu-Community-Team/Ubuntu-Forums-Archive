---
title: "What's wrong with Kernel 3? (Nvidia graphics issues)"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by compiz addict on 2012-07-11
Kernel 3 caused my quite a headache this morning: [http://ubuntuforums.org/showthread.php?p=12093163#post12093163](http://ubuntuforums.org/showthread.php?p=12093163#post12093163)

So the solution was to go back to 2.6.

I really don't mind 2.6, and I forget why I had kernel 3 installed in the first place (perhaps it was a weak attempt at getting my game controller's rumble feature to work).

This is the error I get.
```

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load NVIDIA kernel module. Please check your
(EE) NVIDIA:    system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

```
That, followed by lots of crashing when I choose to "restart X".

So, my real question is: why are my graphics not working properly in kernel 3? It's missing a kernel module, right? Is it easy to add said module? Can I just take it from my 2.6 kernel, or does it even work like that?

---

### Post by darkod on 2012-07-11
Are you trying to install only the kernel or the whole ubuntu OS?

Because 11.10 comes with kernel 3.0 and 12.04 LTS with 3.2.

If you are talking about the whole OS, after you install it (or upgrade to it) there can be issues with some nvidia cards but that it usually solved easily. Basically you need to add the nomodeset boot parameter to allow you to boot once and activate the correct driver. After that it should be fine.

If you are talking about install only kernel 3.0 on a version of ubuntu older than 11.10, I'm not sure how would it work.

---

### Post by compiz addict on 2012-07-11
I'm talking about just the kernel. I installed it a while ago to get a gameport joystick to work in 10.04 (at which point I wasn't aware that you had to update grub after installing a new kernel, so I got quite a surprise when I updated grub for another reason).


Yeah... now that I think about it, the error could entirely be because I'm using the new kernel on the old Ubuntu.

---

