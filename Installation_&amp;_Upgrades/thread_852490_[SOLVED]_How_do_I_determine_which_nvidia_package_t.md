---
title: "[SOLVED] How do I determine which nvidia package to use for my video card?"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by EndingPop on 2008-07-07
I'm having trouble determining whether I should be using the nvidia-glx or nvidia-glx-new drivers. I have an AOpen GeForce 6200 video card. Where can I find out which drivers I should be using? The links below were wonderfully vague.

[http://packages.ubuntu.com/hardy/x11/nvidia-glx]("http://packages.ubuntu.com/hardy/x11/nvidia-glx")
[http://packages.ubuntu.com/hardy/nvidia-glx-new]("http://packages.ubuntu.com/hardy/nvidia-glx-new")

Any help is appreciated.

---

### Post by sdennie on 2008-07-07
I think that card will need the nvidia-glx-new package.  You can probably install it by going to System->Administration->Hardware Drivers.  I believe that will select the right package for you.

---

### Post by stchman on 2008-07-07
> **EndingPop said:**
> I'm having trouble determining whether I should be using the nvidia-glx or nvidia-glx-new drivers. I have an AOpen GeForce 6200 video card. Where can I find out which drivers I should be using? The links below were wonderfully vague.

[http://packages.ubuntu.com/hardy/x11/nvidia-glx]("http://packages.ubuntu.com/hardy/x11/nvidia-glx")
[http://packages.ubuntu.com/hardy/nvidia-glx-new]("http://packages.ubuntu.com/hardy/nvidia-glx-new")

Any help is appreciated.

The restricted driver manager will make that determination for you.

I would say the nvidia-glx-new package, but the nvidia-glx-package will probably work as well.

I am assuming you are running Hardy.

---

