---
title: "Missing xorg.conf???"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by gdanko on 2011-06-23
Hello! I am planning to upgrade my Shuttle XPC (the model escapes me) from Maverick to Natty. It's a standard MicroATX with an Intel dual core 3.something GHz and 4 GB RAM. The video is on-board.

I am posting this message because I performed the same upgrade on my work machine which was also Maverick. I ended up stuck in 1024x768 when normally I was in 1920x1200.  I received an error about how my computer's hardware did not support Unity so use Classic, which is fine. I like Classic. But even switching to Classic I was stuck at 1024 x 768. There was no xorg.conf on the new Natty install for my work computer. After researching the hardware and settings I created one and I am back to normal now.

However, I looked at my Shuttle XPC at home and it has no /etc/X11/xorg.conf either. Where does Maverick store its xorg configuration? I don't want to go through the same pains a second time since this machine at home is also my home server.

Thanks in advance.

---

### Post by dino99 on 2011-06-23
its an old story now, there is no need of xorg.conf (by default, but can built one for special needs like CRT or chipset conflict) as the kernel directly deal with X; Old xorg.conf reused often push the mess.

---

### Post by Grenage on 2011-06-23
> **gdanko said:**
> Hello! I am planning to upgrade my Shuttle XPC (the model escapes me) from Maverick to Natty. It's a standard MicroATX with an Intel dual core 3.something GHz and 4 GB RAM. The video is on-board.

I am posting this message because I performed the same upgrade on my work machine which was also Maverick. I ended up stuck in 1024x768 when normally I was in 1920x1200.  I received an error about how my computer's hardware did not support Unity so use Classic, which is fine. I like Classic. But even switching to Classic I was stuck at 1024 x 768. There was no xorg.conf on the new Natty install for my work computer. After researching the hardware and settings I created one and I am back to normal now.

However, I looked at my Shuttle XPC at home and it has no /etc/X11/xorg.conf either. Where does Maverick store its xorg configuration? I don't want to go through the same pains a second time since this machine at home is also my home server.

Thanks in advance.

xrandr is the preferred way to go, but you can create an xorg.conf if you wish - it will get used.

---

### Post by gdanko on 2011-06-23
> **Grenage said:**
> xrandr is the preferred way to go, but you can create an xorg.conf if you wish - it will get used.

Awesome. So how do I get xrandr to get my machine to use the native 1920x1200? Natty wants to force it to 1024x768.

---

### Post by whatthefunk on 2011-06-23
> **gdanko said:**
> Awesome. So how do I get xrandr to get my machine to use the native 1920x1200? Natty wants to force it to 1024x768.

Check out the xrandr man files.  They are extensive.

---

### Post by gdanko on 2011-06-23
> **whatthefunk said:**
> Check out the xrandr man files.  They are extensive.

All right. Kind of sad I need to read an array of man pages because Ubuntu dropped the ball on the upgrade process.

---

### Post by Grenage on 2011-06-23
> **gdanko said:**
> All right. Kind of sad I need to read an array of man pages because Ubuntu dropped the ball on the upgrade process.

To speed it up:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

A good page, with all you should need; very concise.

---

### Post by gdanko on 2011-06-23
> **Grenage said:**
> To speed it up:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

A good page, with all you should need; very concise.

Perfect, did the trick!

---

