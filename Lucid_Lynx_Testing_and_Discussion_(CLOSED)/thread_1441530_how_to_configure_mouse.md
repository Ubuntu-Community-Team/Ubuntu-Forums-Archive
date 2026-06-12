---
title: "how to configure mouse?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by michaelzap on 2010-03-28
Just got a nice new wireless mouse (a Microsoft Mobile 4000), and I can't figure out how to configure it properly. The scroll speed is too slow (I have to turn the wheel too much), and there's a third button on the left side that I want to be able to use. Anyone know how to configure these settings in Lucid?

---

### Post by sgosnell on 2010-03-28
Have you tried System/Preferences/Mouse?

---

### Post by michaelzap on 2010-03-28
> **sgosnell said:**
> Have you tried System/Preferences/Mouse?

Yes - There are very few settings in there, and the two that I mentioned specifically are not among them.

---

### Post by sgosnell on 2010-03-28
For those functions, I think you'll need Microsoft drivers installed.  Good luck finding Linux drivers for Microsoft products.

---

### Post by VMC on 2010-03-28
That's odd. I just plugged in a Microsoft wireless optical notebook 3000, and my sensitivity is just the opposite. But I prefer being quick than slow. In the past though the mouse preferences worked very well for me.

How about the battery. Is it brand new?

---

### Post by michaelzap on 2010-03-28
> **sgosnell said:**
> For those functions, I think you'll need Microsoft drivers installed.  Good luck finding Linux drivers for Microsoft products.

That sounds overly pessimistic to me. The third button works, but it only does Back (and I want to change that). And I'm sure there must be a standard way to modify the scroll speed, so that shouldn't require anything Microsoft-specific.

---

### Post by Rob2687 on 2010-03-28
Similar problem here. I have the MS 7000 laser mouse. The software in Windows sets the scroll speed on the device. When I boot into Ubuntu the scroll speed is like 5x faster. I have to unplug and plug in the USB transmitter to reset it.

---

### Post by sgosnell on 2010-03-28
I don't think I'm being overly pessimistic.  Even in Windows, you have to run the CD software to get the extra functionality of a mouse, whatever the brand.  You can get basic mouse functions without it, but not all the bells and whistles.

---

### Post by Rob2687 on 2010-03-28
Well you could run xev and see if it captures the button click. Then map it to whatever function you want. I used to do this in 5.04 with some old laptops and those function keys.

Surely there must be a way to adjust the scroll speed. I have searched before but all I found people talking about the unplug/plug USB transmitter solution.

---

### Post by michaelzap on 2010-03-28
> **Rob2687 said:**
> Well you could run xev and see if it captures the button click. Then map it to whatever function you want. I used to do this in 5.04 with some old laptops and those function keys.

Surely there must be a way to adjust the scroll speed. I have searched before but all I found people talking about the unplug/plug USB transmitter solution.

Xev didn't register it, but it works so I probably just need to keep looking for a way to identify and map it. Looks like people used to tweak these settings in xorg, and then later in HAL. But I don't think either of those would work in Lucid.

I'm actually noticing now that the scroll speed is slower on certain web pages (e.g., Google Reader) and not so terrible on others (such as here in the forums).

---

