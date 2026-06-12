---
title: "FF distro-upgrade causes no video signal output"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mverbist on 2007-04-20
I had 2 machines running 6.10
One is a Dell Inspiron 8200 with an nvidia and the other is a custom made with an ATI.
After the distro upgrade they both had the same visible problem: the screen went pitch black and my monitor went to sleep, as if there were no video signal. I'm not sure that internally it is the same cause, although the effect is the same.

I am attaching dmesg, xorg.conf and xorg.log for both computers for anybody who's interested.

**1. For the Dell machine** (dmesg.txt, xorg.conf, xorg.0.log)
I think the relevant lines in dmesg are
[  116.968000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[  116.968000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[  116.968000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!

I think the relevant lines in the log are
6
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce4 440 Go at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.00.55.41
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 440 Go at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 224.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1400x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1400 x 1050
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.


**2. For the ATI machine** (dmesg1.txt, xorg1.conf, xorg1.0.log)
I think the relevant lines in dmesg are
[24124.115926] restricted-mana[6127]: segfault at 0000000000000008 rip 00002b9545567e9c rsp 00007fff67c20eb0 error 4

I think the relevant lines in the log are
(EE) fglrx(0): V_BIOS address 0x0 out of range
(EE) fglrx(0): PreInitInt10 failed
SetVBEMode failed
(EE) fglrx(0): PreInit failed
(

Like I said, although the result is the same for the 2 machines, I'm not sure the cause is the same.

Does anybody have an idea on how to fix this?

---

### Post by K.Mandla on 2007-04-20
For the nvidia card, I've seen a lot of 440s (I have one) that doesn't play well with the 9631 driver that gets installed with Feisty's nvidia-glx driver. Nvidia says it works, but I'm not so sure.

If you like, it's very easy to patch the 8776 driver against Feisty's kernel, and get back full acceleration for your card. Try [this]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386").

I'm afraid I can't speak to the ATI card, though. Sorry. :-?

---

### Post by mverbist on 2007-04-23
Thanks a lot K.

I was finally able to test your solution for the nvidia card on the dell inspiron 8200

I replaced

```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 440 Go]"
    Driver         "nvidia"
EndSection
```

with 

```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 440 Go]"
    Driver         "nvidia"
    Option         "UseDisplayDevice" "DFP"
EndSection
```

And the nvidia card worked.
Once again, thanks.

I'm having some residual problems with the dvd drive that isn't detected anymore, but I'll look into that later.

Someone else an idea for the ATI card?

---

### Post by K.Mandla on 2007-04-23
Hey, I should mention that it might be easier in the future to get that 9631 driver to work. Apparently there's a one-line option you can add to the Device section in your xorg.conf that works. (I've tried it and it works for me, although I want to use it on a clean installation before I give it my blessing. ;) )

Look at [http://www.nvnews.net/vbulletin/showthread.php?t=88951](http://www.nvnews.net/vbulletin/showthread.php?t=88951)

---

### Post by LehighMick on 2007-04-24
I have an Inspiron 8200 w/ GeForce4 440 Go.  This update and fix worked perfectly.  Thank you!!!

Although, it's a little bittersweet bc the 32mb graphics card causes black windows when desktop effects is enabled.  Any suggestions on how to get rid of the black windows, or is it just that my video card is too slow?

Thanks,

Terry

---

