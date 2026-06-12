---
title: "Is compiz borked or something else. Trying to enable desktop effects hangs system."
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-02-09
All you get is wallpaper and the mouse icon going round.

---

### Post by lonerangerls on 2009-02-09
Having similar issues today after last nights upgrade build.

On boot only getting to the wallpaper and then...hangs.

---

### Post by philinux on 2009-02-09
> **lonerangerls said:**
> Having similar issues today after last nights upgrade build.

On boot only getting to the wallpaper and then...hangs.

Right, to get round that one use recovery mode then xfix will get you a normal session. I re-enabled the nvidia driver but trying to enable compiz hangs.And ctry alt backspace is disable doh.

---

### Post by kls96 on 2009-02-09
Bug-Report and some fixes can be found here:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344)

---

### Post by philinux on 2009-02-10
I've disabled compiz for now. Everything working fine 64 and 32 bit.

[edit] just did updates compiz works again but min max and close button are invisible but still work.

---

### Post by plun on 2009-02-10
> **philinux said:**
> I've disabled compiz for now. Everything working fine 64 and 32 bit.

The bug was fixed last night...

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344)


(I had some extra driver mess to sort out8-))

---

### Post by philinux on 2009-02-10
Hi plun, cheers for that, just the title bar glitch to fix now.

Until it breaks again, what fun eh :lolflag:

---

### Post by plun on 2009-02-10
> **philinux said:**
> Hi plun, cheers for that, just the title bar glitch to fix now.

Until it breaks again, what fun eh :lolflag:

Well... you can never know  :^o


The title bar is also mentioned within the bug report.

I am using real stuff, Emerald and it works OK...until it breaks.):P

---

### Post by kj74 on 2009-02-10
> **philinux said:**
> I've disabled compiz for now. Everything working fine 64 and 32 bit.

[edit] just did updates compiz works again but min max and close button are invisible but still work.

That's bug in latest metacity package.

---

