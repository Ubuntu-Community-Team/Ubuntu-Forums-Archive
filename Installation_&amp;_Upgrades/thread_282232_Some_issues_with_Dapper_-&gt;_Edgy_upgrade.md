---
title: "Some issues with Dapper -&gt; Edgy upgrade"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by KLineD on 2006-10-22
I recently did an upgrade from Dapper to Edgy and I'm having some trouble mainly with my wireless network card. It's an Intel PRO/Wireless 3945ABG (laptop) and it works just fine in Dapper. In fact it works fine in edgy too but using kernel 2.6.17-10-386. If I use the generic kernel my card doesn't gets detected at boot time.

The problem is that I need a 686 kernel so Linux can use both cores in my processor. The generic kernel uses both cores with no problem, but I'm left with no wireless.

Also, although minor, I can't see the boot splash screen. All that I see is some blue and green garbage lines at the bottom of the screen. My video card is an ATi mobility radeon X1400 (3D accel is not working btw, it all worked fine in Dapper)

Is there going to be a 2.6.17-10-686 kernel, or should I stick with the generic one and try to fix the wireless issues?

Thanks!

---

### Post by pradeepadapa on 2006-10-22
hi man,

    why dont u upgrade ur kernel to the latest stable version 2.6.18, nd try it it may work.

---

### Post by KLineD on 2006-10-22
Hi! thanks for your reply. Actually I just found out that I was missing the restricted modules for the generic kernel. DOH!

So I did apt-get install linux-restricted-modules-generic and now wireless and both cores get along.

The only thing that's missing is the bootscreen... all I can see is black. Any ideas?

---

### Post by pradeepadapa on 2006-10-22
hi,

what d u mean by not getting boot screen, r u not getting grub screen or after that.

---

### Post by KLineD on 2006-10-22
Yeah something among those lines. After grub screen in Dapper I would see a brown ubuntu logo and a progress bar with some text underneath it. Now I don't see anything just some blue and green garbage lines at the bottom of the screen. The machine boots fine and GDM shows just fine, it's just that boot splash screen that is missing.

---

### Post by pradeepadapa on 2006-10-23
hii,

         then there is absolutely no problem to panic, even i hav the same problem but it is fine with me since it boots up in less than a minute. dont panic.

---

### Post by KLineD on 2006-10-23
Yeah I know... but still I would like to have 3D acceleration with my ati card. In dapper I used fglrx and it is installed in edgy but fglrxinfo gives me:
> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

---

