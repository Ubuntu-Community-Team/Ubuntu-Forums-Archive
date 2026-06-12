---
title: "About ATI drivers in Lucid"
date: 2010-02-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Speed_arg on 2010-02-28
When I booted Alpha 3 live cd, compiz was enabled with some effects, and rendering worked fine, unlikely previous versions which without drivers would suck and not enable you to use compiz.

Now my question is, does lucid bring ATI drivers out of the box? Or what? I read about the nouveau stuff, but thats for NVIDIA only, isn't it?

---

### Post by aamukahvi on 2010-02-28
> **Speed_arg said:**
> When I booted Alpha 3 live cd, compiz was enabled with some effects, and rendering worked fine, unlikely previous versions which without drivers would suck and not enable you to use compiz.

Now my question is, does lucid bring ATI drivers out of the box? Or what? I read about the nouveau stuff, but thats for NVIDIA only, isn't it?

The open-source driver for ATI is maturing, that's all.
[http://www.phoronix.com/scan.php?page=article&item=ati_r600_mesa_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r600_mesa_3d&num=1)

---

### Post by andrek on 2010-02-28
If only it had gpu power management support.. The lack of it sucks for laptop users.

---

### Post by uBeer on 2010-02-28
> **andrek said:**
> If only it had gpu power management support.. The lack of it sucks for laptop users.

My battery is broken anyways (36.9% capacity left - 20 min) so I don't mind, I have to use the power cable anyways. The only problem for me is a slightly warmer laptop.

---

### Post by antiram on 2010-02-28
you could use some of the pm options in /etc/X11/xorg.conf, eg.
```

Section "Device"
        Driver          "radeon"
        Identifier      "Configured Video Device"

        Option          "ClockGating"           "on"
        Option          "DynamicPM"             "on"
        Option          "ForceLowPowerMode"     "on"
EndSection

```
a initial xorg.conf can be made with
sudo dpkg-reconfigure -phigh xserver-xorg
or so

---

### Post by andrek on 2010-02-28
Do these options work with KMS enabled? Also, do they make the fan go as slow as fglrx does?

I'm afraid not, but thanks anyway.

---

### Post by antiram on 2010-02-28
i used this options some month ago with karmic and xorg-edgers without kms.

---

### Post by t.alex on 2010-02-28
proper kms power management should come with 2.6.34. just wait another week for rc1 :popcorn:

---

### Post by uBeer on 2010-02-28
> **antiram said:**
> i used this options some month ago with karmic and xorg-edgers without kms.

And did the options help? Was there a performance penalty? I guess for normal desktop (actually laptop ;) ) use it didn't make any difference?

Edit: Alas, it's not working for me:
```
[    0.155408] (WW) RADEON(0): Option "ClockGating" is not used
[    0.155422] (WW) RADEON(0): Option "DynamicPM" is not used
[    0.155432] (WW) RADEON(0): Option "ForceLowPowerMode" is not used
```

Guess I'll have to wait for the 2.6.34 kernel...

---

### Post by andrek on 2010-02-28
The worst thing is that the laptop goes quickly hot and loud - thanks to its fans. I hope 2.6.34 kernel will fix that issue.

---

### Post by zika on 2010-02-28
> **uBeer said:**
> And did the options help? Was there a performance penalty? I guess for normal desktop (actually laptop ;) ) use it didn't make any difference?

Edit: Alas, it's not working for me:
```
[    0.155408] (WW) RADEON(0): Option "ClockGating" is not used
[    0.155422] (WW) RADEON(0): Option "DynamicPM" is not used
[    0.155432] (WW) RADEON(0): Option "ForceLowPowerMode" is not used
```Guess I'll have to wait for the 2.6.34 kernel...Did You try putting **options radeon dynclks=1** in **/etc/modprobe.d/radeon-kms.conf** ...?

---

### Post by uBeer on 2010-02-28
No, I actually do not have that file there. Can I just create that file with only that line in it or do I have to put more stuff in it?

Edit: cat /sys/module/radeon/parameters/dynclks now returns 1, but the frequency listed by cat /sys/kernel/debug/dri/64/radeon_pm_info doesn't change, and I still get the same messages in Xorg.0.log about not loading the modules.

I must note that I have the stock Lucid kernel, 2.6.32. Do I have to install the 2.6.33 for some of these features? You said you had it working on Karmic so I guess that it should work on 2.6.32 as well...

---

### Post by boolean_ on 2010-02-28
(WW) RADEON(0): Option "ClockGating" is not used
(WW) RADEON(0): Option "DynamicPM" is not used
(WW) RADEON(0): Option "ForceLowPowerMode" is not used

I'm getting a real head ache from my video card fan. If anyone has any ideas of how to solve this I would be grateful.

Tried everything in this thread so far but still 100% fan speed...

---

### Post by antiram on 2010-02-28
> **uBeer said:**
> I must note that I have the stock Lucid kernel, 2.6.32. Do I have to install the 2.6.33 for some of these features? You said you had it working on Karmic so I guess that it should work on 2.6.32 as well...
i used the .31 karmic kernel only 2 weeks then .32 later .33-rc4 and newer.

if this is so essential for laptops you can use usermode settings, eg. kernelparameter "nomodeset" or "radeon.modeset=0" or similar setting in the radeon-kms.conf.

the forcelowpowermode brings the most powersaving. 3-5 Watt for me with a hd3450 (desktop with "voltcraft energy check 3000"). Linux graphic was fast, no slowdowns to see with compiz. But i use some hours per day a win xp install over rdesktop rdp and the rdp was clearly slower. Too slow for 3-5 Watt energy saving on a desktop.

---

### Post by uBeer on 2010-02-28
Ah: [http://www.mail-archive.com/xorg-driver-ati@lists.x.org/msg12211.html](http://www.mail-archive.com/xorg-driver-ati@lists.x.org/msg12211.html)

Apparently enabling KMS makes the power management go into the kernel and not in X. So I guess we do have to wait if we want to make use of kms...

---

### Post by zika on 2010-03-01
> **antiram said:**
> if this is so essential for laptops you can use usermode settings, eg. kernelparameter "nomodeset" or "radeon.modeset=0" or similar setting in the radeon-kms.conf.**options radeon modeset=0** in **/etc/modprobe.d/radeon-kms.conf**.
If You choose to put nomodeset or radeon.modeset=0 in Your kernel-line, then file radeon-kms.conf might return error since it is used only if kernel doesn't have KMS disabled (enable/disable order while booting)...

---

