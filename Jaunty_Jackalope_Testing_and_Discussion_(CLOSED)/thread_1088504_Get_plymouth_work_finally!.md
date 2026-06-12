---
title: "Get plymouth work finally!"
date: 2009-03-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by portis on 2009-03-06
I'm using an Intel 965 laptop.

I recompiled 2.6.29 rc7 kernel with i915 and fbcon compiled into the kernel, and of course KMS enabled by default. The fbcon is also important, without it, you cannot do the VT-switch, and plymouth doesnot work correctly. The precompiled kernel in [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc7/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc7/") doesnot enable KMS, so you have to compile it yourself.

Now plymouth works great. I can see the animation just as shown in this [video]("http://www.youtube.com/watch?v=a1U0dK2HpUk"). I can also do the VT-switch smoothly.

Still a problem, some functionalities of xrandr no longer work. I cannot switch off LVDS1 monitor by xrandr --output LVSD1 --off. This bug has been fired already, have to wait...

---

### Post by Tich666 on 2009-03-06
Great news.
However xrandr to me is more important than plymouth atm and I'm pretty sure compiling the kernel myself is a little bit out of my league still, so I'll have to stick with usplash for now. :(

I'd be interested in getting KMS to work for reasons other than plymouth though, but I'm hopeful that the situation is going to improve.

---

### Post by autocrosser on 2009-03-06
Well, its a bit late for Jaunty --the next development cycle will be seeing work on this front--So we all have to wait for Karmic to start up--less that 2 months to go............

---

### Post by KhaaL on 2009-03-06
great to hear! excuse my ignorance, but what does the VT switch do?

---

### Post by portis on 2009-03-06
Virtual terminal switch.

> **KhaaL said:**
> great to hear! excuse my ignorance, but what does the VT switch do?

---

### Post by jfernyhough on 2009-03-06
That looks sweet. If I had such a nice animation I wouldn't worry as much about boot up time! :D

Just a shame there's still an ugly GRUB and flicker as X loads. But it looks good so far!

---

### Post by portis on 2009-03-06
You can use GRUB2 to get a pretty boot menu.

> **jfernyhough said:**
> That looks sweet. If I had such a nice animation I wouldn't worry as much about boot up time! :D

Just a shame there's still an ugly GRUB and flicker as X loads. But it looks good so far!

---

