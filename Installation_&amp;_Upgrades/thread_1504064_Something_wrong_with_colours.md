---
title: "Something wrong with colours"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by peligro on 2010-06-07
Hi. When i boot from CD i got this: 
[http://img20.imageshack.us/i/1000841d.jpg/](http://img20.imageshack.us/i/1000841d.jpg/)
After that i loads to another window:
[http://img704.imageshack.us/i/1000840vx.jpg/](http://img704.imageshack.us/i/1000840vx.jpg/)
Than green thing is my mouse :\
Help please :( If you need more information ask me. :(

---

### Post by FuturePusher on 2010-06-07
Hi peligro!


*Sigh*.. I'm wondering if Your issue is due to that pesky "EFI" framebuffer driver ("efifb"), which the bootloader GRUB2 (newer GRUB, now default in Ubuntu Lucid Lynx) seems to instruct the kernel to initialize and boot with.

I'm on integrated Nvidia graphics (8300) with Nvidia's proprietary driver, works excellent in X on my Jaunty (Ubuntu 9.04)...
The only thing is that since I upgraded from "grub-legacy" to "grub-pc" (GRUB2)... the color white is now light green in my framebuffer-driven consoles - and upon some research, it seems it's due to inadeqacies (slight incompatibility with Nvidia, and possibly ATI graphics hardware) in this "EFI" framebuffer driver.

I draw this conclusion because I used to be running "vesafb" (that's; VESA framebuffer)... and when checking the file @ /proc/fb (shows wich framebuffer driver is actually in use)... **it shows this "EFI" framebuffer** - GRRR! My choice of using "vesafb" was totally overridden by GRUB2's video/graphics handling.. I hate dictatorship! :mad:


Anyhow, since You say You're booting from an intall-cd, I'm strongly suspecting it's all just using framebuffer-based graphics, as opposed to initialising a proprietary driver for Your hardware, which in these days is most likely to be either Nvidia or ATI... right?

And since we're talking about Lucid Lynx (10.04), with GRUB2, You can most likely also hold the "EFI" framebuffer driver responsible for graphics artifacts on modern-day graphics hardware, normally requiring a non-OpenSource/proprietary driver for full hardware acceleration & features.

[INDENT]
[COLOR="DarkRed"]So, here's a tip for You to try (hopefully enough of some of the other things Your system requires for this to function, are already in place - spontaneously, I'm thinking of un-blacklisting "vesafb" in "/etc/modprobe.d/blacklist-framebuffer" and making sure it's in Your initramfs/init-image ("modprobe vesafb", and then "update-initramfs -vck all")...) :

* Have "video=vesafb" (no quotes) added as a kernel parameter in GRUB2's configuration, unfortunately: how You should do this is kind of a chapter of it's own...[/COLOR][/INDENT]


NOTE:
Unfortunately, this can obviously likely only be done once You've managed to do an installation, and not on the install-CD!
(Technically speaking, it's fully possible to temporarily add this kernel parameter if the install-CD starts up GRUB for You, by editing the kernel command line... but I wouldn't hope for it to work, since the more properly functioning "vesafb" framebuffer driver is probably NOT included in the install-CD's initramfs/init-image... quite typical, huh?)

Again: *sigh*...

---

