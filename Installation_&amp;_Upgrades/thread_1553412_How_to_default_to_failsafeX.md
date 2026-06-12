---
title: "How to default to failsafeX"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by davidoz on 2010-08-15
I've installed UNR 10.04 on an old UMPC. Graphics are a total mess, even console text doesn't display properly. All I get is a bunch of pixels, smeared across the screen.

I'd blame KMS, but that's only supposed to affect X. Anyway, according to [https://wiki.ubuntu.com/X/KernelModeSetting/](https://wiki.ubuntu.com/X/KernelModeSetting/), "KMS is enabled by default for the -intel, -ati, and -nouveau drivers. It is not available for any other drivers". Mine isn't any of those, so KMS shouldn't be enabled at all.

I've found that failsafeX in a recovery console works OK. My question is, how can I get UNR 10.4 to default to failsafeX in normal mode?

---

### Post by dino99 on 2010-08-15
try this:

sudo gedit /etc/default/grub

then set GRUB_DEFAULT=1 (instead of 0)

save and close, then: sudo update-grub

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by kerry_s on 2010-08-15
when you say "failsafeX" you mean the vesa drivers?

---

### Post by davidoz on 2010-08-15
> **dino99 said:**
> try this:

sudo gedit /etc/default/grub

then set GRUB_DEFAULT=1 (instead of 0)

Thanks. That sets the default to the recovery console. What I'm trying to achieve is failsafeX in a normal login.

> **kerry_s said:**
> when you say "failsafeX" you mean the vesa drivers?

In the recovery console, there's a menu option labeled failsafeX. Whatever that is, it's what I want (at least until I can get something better to work).

---

### Post by davidoz on 2010-08-16
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-xorg-extract-failsafex](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-xorg-extract-failsafex) indicates that failsafeX is more than just a driver. I don't understand 90% of that page, but the information might clarify things for someone who knows more than I do.

---

### Post by kerry_s on 2010-08-16
i think thats vesa.

boot into recovery mode, select root shell.
type-> X -configure

this will make a xorg.conf that you can copy to /etc/X11/xorg.conf

change the driver line in there to use "vesa".

---

### Post by davidoz on 2010-08-17
Thanks Kerry,

That worked. As far as I could tell, there wasn't an /etc/X11/xorg.conf before I copied /root/xorg.conf.new (which X -configure created) there. That file listed the openchrome driver, which is appropriate to my hardware and worked in previous versions of Ubuntu, but didn't work this time. The vesa driver works fine.

In /etc/X11, I noticed a file xorg.conf.failsafe, the Device section of which lists the vesa driver. Evidently, failsafeX is mostly (if not entirely) vesa, as you suggested.

---

### Post by kerry_s on 2010-08-17
now you know failsafeX creates a "xorg.conf.failsafe" next time all you have to do is just rename that file to "xorg.conf".

---

### Post by davidoz on 2010-08-17
The contents of xorg.conf.failsafe are minimal. It looks generic.

Renaming or copying the file to xorg.conf might work, but there'd be a lot missing that's probably necessary. Renaming it also risks disabling failsafeX for the recovery console.

Your original suggestion yields a far better (semi-)permanent solution.

---

