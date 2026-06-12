---
title: "Buggy intel graphics driver after update"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by finni on 2010-01-23
I own a HP nx7400 laptop with Intel integrated 945GM graphics. I updated from Ubuntu 32bit jaunty 9.04 to 32bit karmic 9.10 with update-manager and after that intel driver seems to hang the system randomly when I plug an external monitor to the laptop and use 'gnome-display-properties' to try to activate the monitor (mirroring laptop screen and same resolution monitor). The monitor now gets a signal, but both the screens go black and ubuntu is now unresponsive and I have to boot manually by holding power-off -key from the laptop. 

Does anyone have a solution to this?

---

### Post by finni on 2010-01-24
> **finni said:**
> I own a HP nx7400 laptop with Intel integrated 945GM graphics. I updated from Ubuntu 32bit jaunty 9.04 to 32bit karmic 9.10 with update-manager and after that intel driver seems to hang the system randomly when I plug an external monitor to the laptop and use 'gnome-display-properties' to try to activate the monitor (mirroring laptop screen and same resolution monitor). The monitor now gets a signal, but both the screens go black and ubuntu is now unresponsive and I have to boot manually by holding power-off -key from the laptop. 

Does anyone have a solution to this?

Anyone?

Now it also seems to hang the system when monitor is turned off to save power on the laptop.

---

### Post by finni on 2010-01-30
I'm not sure if it's the intel graphics driver, the gnome screen "applet" or Xorg problem.

Anyone else experiencing this?

---

### Post by lamba_lam on 2010-01-30
> **finni said:**
> I'm not sure if it's the intel graphics driver, the gnome screen "applet" or Xorg problem.

Anyone else experiencing this?

i am i have intel 845 motherboard i am pretty sure i am having same problem. every hour or 2 i have to reset the system. nothing works.
i am trying out lucid btw.

---

### Post by falconindy on 2010-01-30
> **lamba_lam said:**
> i am i have intel 845 motherboard i am pretty sure i am having same problem. every hour or 2 i have to reset the system. nothing works.
i am trying out lucid btw.
Your issue is likely unrelated to the OP's. Lucid's kernel (2.6.32) is currently hell on Intel graphics.

@OP: If you're using KMS, consider enabling it. If you are using it, disable it. Yes I understand this may seem odd, but KMS is somewhat buggy and seems to perform differently on every Intel chipset.

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by lamba_lam on 2010-01-30
> **falconindy said:**
> Your issue is likely unrelated to the OP's. Lucid's kernel (2.6.32) is currently hell on Intel graphics.


o_O should i go back to 9.10 then?

---

### Post by falconindy on 2010-01-30
> **lamba_lam said:**
> o_O should i go back to 9.10 then?
You get the same advice that the OP did. The only difference is that in 2.6.31, KMS is **disabled** by default. In 2.6.32, KMS is **enabled** by default.

---

### Post by lamba_lam on 2010-01-31
> **falconindy said:**
> You get the same advice that the OP did. The only difference is that in 2.6.31, KMS is **disabled** by default. In 2.6.32, KMS is **enabled** by default.

o i see but the thing is i am new so i don't know how to disable KMS. please through some light. :)

---

### Post by falconindy on 2010-01-31
Follow the same instructions from the wiki link above. Wherever they mention i915.modeset=1, just replace the 1 with a 0.

---

### Post by lamba_lam on 2010-01-31
> **falconindy said:**
> Follow the same instructions from the wiki link above. Wherever they mention i915.modeset=1, just replace the 1 with a 0.
actually i was about to do that but was afraid and decided to ask. Thanks for your help. :D

---

### Post by finni on 2010-02-03
I will try enabling KMS today. I have 2.6.31-17 kernel.

---

### Post by finni on 2010-02-17
> **finni said:**
> I will try enabling KMS today. I have 2.6.31-17 kernel.

It still hangs occasionally, but less than with having KMS disabled.

---

