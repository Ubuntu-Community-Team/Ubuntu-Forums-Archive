---
title: "Graphic card drivers"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by WeldonJ92 on 2013-01-26
I am a new user of Ubuntu and have very little understanding of how it works.

I have installed Ubuntu 12.10.
I am running Ubuntu 12.10 on a HP Pavilion G6.
The graphic card this laptop uses is a AMD Radeon HD 6480G.
Ubuntu is not using the graphic card driver that it should be.
Instead I think it is using 'vesa', which I think is a very low 2D-specific graphic driver.

I have already searched for how to install this.

I know how to open the 'terminal' and I know that sudo is something about installing and that sometimes I am prompted for a password.

If someone knows how to install these drivers, that would be brilliant.
I would like to use Ubuntu, however if these drivers won't install, then I can't. :/

Thanks a lot!

- Jake.

Edit:
A website said that my graphic driver was something else, which I did eventually install I think, but then Ubuntu would not boot and would hang at a black screen with a blinking white cursor. I then booted Ubuntu in graphic safe mode, but this did not work either.
I then found information suggesting that my graphic driver is something other than what a website had said.
Since then I have uninstalled Ubuntu and installed a fresh copy of Ubuntu.
I have not changed anything within this copy of Ubuntu and am waiting for someone more knowledgeable than myself to explain. :)

---

### Post by Cheesemill on 2013-01-26
You don't need to use the terminal at all. Just go to System Settings > Software Sources > Additional Drivers and choose the driver for your graphics card.

---

### Post by WeldonJ92 on 2013-01-26
> **Cheesemill said:**
> You don't need to use the terminal at all. Just go to System Settings > Software Sources > Additional Drivers and choose the driver for your graphics card.

I will try that in a few minutes.
I hope it works. :)
Thank you.

- Jake.

---

### Post by WeldonJ92 on 2013-01-26
> **Cheesemill said:**
> You don't need to use the terminal at all. Just go to System Settings > Software Sources > Additional Drivers and choose the driver for your graphics card.

Hey.

There are 3 additional drivers.
- Using X.org X server - AMD/ATI display driver wrapper from xserver-xorg-video-ati (open source, tested)
- Using video driver for the AMD graphics accelerators from fglrx (proprietary)
- Using video driver for the AMD graphics accelerators from fglrx-updates (proprietary)

Which one should I use?

Thanks a lot.

- Jake.

---

### Post by Cheesemill on 2013-01-26
Try the second one (fglrx).

---

### Post by WeldonJ92 on 2013-01-26
> **Cheesemill said:**
> Try the second one (fglrx).

Okay, in the details window it says:

Driver: Unknown
Experience: Standard

Should I restart the computer?

Thanks. :)

---

### Post by WeldonJ92 on 2013-01-26
> **Cheesemill said:**
> Try the second one (fglrx).

The graphics have changed to VESA now.. :/

The graphics were actually working better until I did that.
Now they are lagging.. o.o
Haha..

---

### Post by WeldonJ92 on 2013-01-26
No one has any idea?

---

