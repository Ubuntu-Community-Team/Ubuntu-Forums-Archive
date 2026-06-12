---
title: "Glitchy video after install."
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by wh33t on 2012-05-24
Ok so this is super weird.

If I do the "try Ubuntu" the graphics look crisp and beautiful. But then during the install from the graphical environment as soon as the installer installs some graphic drivers (I'm assuming that's when it's messing up) the graphics instantly become glitchy and pixelated and the computer becomes impossible to use.

Is this a common issue?

The laptop I'm installing it on is a Gateway LT31 netbook. Here is it's specs [http://support.gateway.com/s/notebook/2009/gateway/lt/lt31/LT31sp2.shtml](http://support.gateway.com/s/notebook/2009/gateway/lt/lt31/LT31sp2.shtml).

---

### Post by wh33t on 2012-05-24
> **wh33t said:**
> Ok so this is super weird.

If I do the "try Ubuntu" the graphics look crisp and beautiful. But then during the install from the graphical environment as soon as the installer installs some graphic drivers (I'm assuming that's when it's messing up) the graphics instantly become glitchy and pixelated and the computer becomes impossible to use.

Is this a common issue?

The laptop I'm installing it on is a Gateway LT31 netbook. Here is it's specs [http://support.gateway.com/s/notebook/2009/gateway/lt/lt31/LT31sp2.shtml](http://support.gateway.com/s/notebook/2009/gateway/lt/lt31/LT31sp2.shtml).

I should also note, this doesn't happen with older versions of Ubuntu. I have tried Ubuntu 9.04 and it worked fine.

I've also tried Ubuntu 10.04 and Xubuntu 11.10 and they both caused the same issues. So it must have something to do with a different display adapter or something that has come out in recent versions.

---

### Post by wh33t on 2012-06-06
* Bump *

No one has any clue what this issue is? 

Can anyone out there even tell me simply how to disable the graphic driver so I can use the Laptop with out graphic acceleration? I'd settle for that right now.

Please, anyone?

---

### Post by Basher101 on 2012-06-06
Could you post your hardware specifications? I don't think many will be able to help if they do not know what hardware you are trying to install Ubuntu on

---

### Post by wh33t on 2012-06-06
> **Basher101 said:**
> Could you post your hardware specifications? I don't think many will be able to help if they do not know what hardware you are trying to install Ubuntu on

The specs are linked in the original post. Thank you for trying.

I'll also add, this garbled video glitch thing happens on any version past 9.04. So there must have been some kind of graphic driver change for my specific video adapter.

---

### Post by Basher101 on 2012-06-06
> **wh33t said:**
> The specs are linked in the original post. Thank you for trying.

I'll also add, this garbled video glitch thing happens on any version past 9.04. So there must have been some kind of graphic driver change for my specific video adapter.

seems to be more of a Kernel issue than graphics driver issue

From what i see you have some sort of onboard graphics (they are typical for specs like shared memory). I have no expirience with anything ATI related, yet alone their onboard graphics. Hope someone who has the knowledge to help you comes across...good luck further on


regards

---

### Post by QIII on 2012-06-06
Before anyone suggests it, don't install the fglrx (ATI) driver.  Your hardware is no longer supported by the current Linux driver and the legacy driver will no longer work with X server.

You will probably need to use "nomodeset" as a kernel option, although that seems more common with NVIDIA cards.  Given the legacy status of yours, it may be required.  It's worth a try.

[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by wh33t on 2012-06-06
> **QIII said:**
> Before anyone suggests it, don't install the fglrx (ATI) driver.  Your hardware is no longer supported by the current Linux driver and the legacy driver will no longer work with X server.

You will probably need to use "nomodeset" as a kernel option, although that seems more common with NVIDIA cards.  Given the legacy status of yours, it may be required.  It's worth a try.

[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")

Thank you. I'll try that out.

Would it be foolish of me to think that this kind of thing would be automatically detected during install? Isn't there some kind of utility that probes hardware to see what is supported and what isn't?

---

### Post by QIII on 2012-06-06
No and sort of, respectively.  There are only so many testers that can be hired by a relatively small company that gives its product away for free while depending on revenue from service contracts only.

---

