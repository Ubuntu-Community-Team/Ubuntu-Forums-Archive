---
title: "Ubuntu is reporting color setting at 16.7M but its either 256 or 65K."
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Havage on 2009-10-14
So, I just got the rev 185 drivers to function with my fresh install of 9.10 and a NVidia Gefore 9500GT vid card but the colors don't look right.

All graphical acceleration looks fine (Compiz runs quick and clean) and the NVidia app is reporting 16.7M colors but when I look at pictures or browse the web, it is clear that I'm either in 256 or 65K color mode.

Any ideas?

Thanks,
Leo

---

### Post by FuturePilot on 2009-10-14
Are you using a DVI connection by chance?

---

### Post by Havage on 2009-10-14
Why yes, yes I am FuturePilot, is there a problem with this?

---

### Post by FuturePilot on 2009-10-14
> **Havage said:**
> Why yes, yes I am FuturePilot, is there a problem with this?

I'm not sure, but I think I've run into the same exact issue as you. I've had this problem since Hardy. I noticed that it goes away if you use VGA. Do you have a DVI to VGA adaptor you could test?

---

### Post by Havage on 2009-10-14
Good news - Colors look better (more blending less obvious boundaries between colors)
Bad news - Text is fuzzy 

I hooked up the VGA cable to the linux box and the DVI cable to a Vista box.
Browsed both to this page and this:
[http://resa.linux-hardcore.com/wp-content/uploads/2009/10/KarmicKoala-LoginScreen-SunVirtualBox.png]("http://resa.linux-hardcore.com/wp-content/uploads/2009/10/KarmicKoala-LoginScreen-SunVirtualBox.png")

Page. The image looks better with the DSub connection but the text looks way better on the DVI connection. 

Now the question is, do I want a headache from reading blurry text or a headache from looking at crappy images. Either case sucks :P

**EDIT**

So, the problem is "fixed", I went back to the DVI connection on the monitor and decided to go into the monitors settings themselves and tamper with the color levels and such. I couldn't find a "reset to default" so I just messed with them myself and after lowering the *red* level the blending became much better.

Thanks for the help, I had no idea that that could have been the cause.

---

### Post by null_pointer_us on 2009-10-14
Digital Vibrance (in Nvidia driver settings app) can severely limit your color ranges, especially if you set it to a fairly high value. It's possible that switching from DVI to VGA reset your Digital Vibrance to zero, which could have made the problem go away, too.

LCD panels supporting VGA connections usually have an "auto adjust" button (or OSD menu item) somewhere that can greatly improve image quality, especially for computer text. This can reduce many geometry/sync issues.

---

### Post by Havage on 2009-10-14
Very good answer - that is exactly what I think did it. I changed the cables back and forth then pressed the autoset button (which I thought did nothing) but afterwards everything worked!

Thanks,
Leo

---

