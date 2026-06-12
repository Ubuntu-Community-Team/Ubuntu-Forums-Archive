---
title: "nVidia Drivers causing resolution issues with terminals."
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Tynach on 2010-05-02
You know, the "ctrl+alt+F5" type things, where you go to those pure command lines?

I installed Ubuntu 10.04 from scratch, and everything was working great! Good resolution, etc. When I booted up my computer, the (very brief) splash screen fit the entire resolution of my monitor (1680x1050), and the X server did the same.

When I'd go to one of those 'tty' terminals, I was surprised (in a good way) to see that they had scaled to my monitor's resolution as well. I was looking forward to using that.

Well, time came where I wanted to turn on Compiz, so I downloaded/installed the nVidia drivers.

Well, they work. I can work with Compiz and 3D games at full speed and full resolution in Ubuntu, and I have zero complaints about that.

What I do have a complaint about is that the terminals (tty5, in the above example) are back to that old resolution, 640x480 I believe. Also, that brief splash screen is at the same horrible resolution, instead of the full resolution I had on the old nVidia driver that didn't support 3D effects.

Is there a way to get that back? Is it a bug or a glitch that it's no longer scaling the tty's to my display resolution, and do I just have to wait for an update?

---

### Post by bowens44 on 2010-05-02
I can't help you with the ugly splash screen. That is an issue with Plymouth and the proprietary nvidia drivers. Personally, I don't use a splash screen, I like to see what is happening during the boot up and shut down process so I turn it off.

As far as getting the correct resolution in the virtual terminals, I followed the instructions at this link:

[http://lab.frontseed.com/entry/enable-frambeuffer-ubuntu-karmic-koala-using-grub2](http://lab.frontseed.com/entry/enable-frambeuffer-ubuntu-karmic-koala-using-grub2)

It says it's for karmic but works for lucid too.

---

### Post by Tynach on 2010-05-02
Well, I had my doubts, but that went above and BEYOND my problem!

It solved both my complaints, AND it made GRUB use my full monitor resolution! WOW!

---

### Post by Lurkos on 2010-05-06
It didn't work for me! :-(
I've added vga=0x161 to grub loader configuration, since I'm using grub-legacy.

---

